TugasBesarFileIndexer
=====================

package tubesstrukdat;

class Elemen {

    String data;
    String path;
    String contains;
    Elemen next;
    Elemen prev;
}

public class DoubleLinkedList {

    Elemen head;
    Elemen tail;
    int jumlahElemen = 0;

    boolean isEmpty() {
        return (head == null & tail == null);
    }

    void IsiNext(String data, String path, String contains) {
        Elemen tmp = new Elemen();
        tmp.data = data;
        tmp.path = path;
        tmp.contains = contains;

        if (isEmpty()) {
            head = tmp;
        } else {
            tail.next = tmp;
            tmp.prev = head;
        }
        tail = tmp;

    }

    void IsiPrev(String data) {
        Elemen tmp = new Elemen();
        tmp.data = data;

        if (isEmpty()) {
            tail = tmp;
        } else {
            head.prev = tmp;
            tmp.next = tail;
        }
        tmp = head;


    }

    void BacaDariDepan() {
        Elemen tmp = head;
        while (tmp != null) {
            System.out.println(tmp.data);
            System.out.println(tmp.path);
            tmp = tmp.next;
        }
    }

    void BacaDariBelakang() {
        Elemen tmp = tail;
        while (tmp != null) {
            System.out.println(tmp.data);
            tmp = tmp.prev;
        }
    }

    String cariPath(String data) {
        Elemen tmp = head;
        String returnVal = "";

        while (tmp != null) {
//            System.out.println(tmp.contains);
            if (tmp.contains.contains(data)) {
                returnVal += tmp.path + "\n";
            }
            tmp = tmp.next;
        }

        return returnVal;
    }

    Elemen CariElemen(int index) {
        Elemen tmp;

        if (index < (jumlahElemen / 2)) {
            System.out.println("Dari Depan");
            tmp = head;
            for (int i = 0; i < index; i++) {
                tmp = tmp.next;
            }
        } else {
            System.out.println("Dari Belakang");
            tmp = tail;
            for (int i = jumlahElemen; i > index; i++) {
                tmp = tmp.prev;
            }
        }
        return tmp;
    }

    void IsiTengah(int index, String data) {
        Elemen tmp = new Elemen();
        tmp.data = data;

        Elemen posisi = CariElemen(index);
        tmp.prev = posisi;
        tmp.next = posisi.next;
        posisi.next.prev = tmp;
        posisi.next = tmp;
        jumlahElemen++;
    }

    void hapustengah(int index, int data) {
        Elemen tmp = CariElemen(index);

        tmp.prev.next = tmp.next;
        tmp.next.prev = tmp.prev;
        tmp.prev = null;
        tmp.next = null;
        jumlahElemen--;
    }
}
