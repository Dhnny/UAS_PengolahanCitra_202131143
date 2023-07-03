
# Ujian Akhir Semester Pengolahan Citra

Pada Projek uas kali ini adalah membuat segmentasi Kata dengan menggunakan gambar hasil jepretan sendiri pada handphone masing-masing yang dimana pada projek kali ini menggunakan bahasa pemrograman python dengan aplikasi jupyter notebook serta menggunakan library OpenCV dan pytesseract/tesseract sebagai file headernya.

# Memanggil OpenCV dan tesseract
import cv2

import pytesseract

perintah di atas adalah cara mengimport atau memasukkan library yang akan digunakan menjadi file header pada projek kali ini dan dibutuhkannya pytesseract adalah sebagai pendukung untuk melakukan word recognition atau pengenalan bentuk kata pada sebuah gambar

# Memanggil gambar dan mengkonversi
pytesseract.pytesseract.tesseract_cmd = 'C:\\Program Files\Tesseract-OCR\\tesseract.exe'

img = cv2.imread('Dani2.jpeg')

img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
print(pytesseract.image_to_boxes(img))

cv2.imshow('Result',img)

cv2.waitKey(0)

inputan di atas adalah cara untuk memanggil gambar yang ingin kita lakukan segmentasi kata dan kali ini saya menggunakan judul "Dani2" dengan format jpeg yang kemudian akan diubah menjadi format RGB dan mencetak gambar menjadi kotak dalam perintah pytesseract.

# Segmentasi Kata
hImg,wImg,_ = img.shape

boxes = pytesseract.image_to_boxes(img)

for b in boxes.splitlines():

    print(b)
    b = b.split(' ')
    print(b)
    x,y,w,h = int(b[1]),int(b[2]),int(b[3]),int(b[3])
    cv2.rectangle(img, (x,hImg-y), (w,hImg-h),(0, 0, 255),2)

cv2.imshow('Result',img)

cv2.waitKey(0)

Perintah di atas adalah memanggil kotak sebagai penanda dan pemisah kata yang di segmentasi yang dimana untuk bentuk dari gambar tersebut dipanggil menjadi hImg (tinggi) dan wImg (lebar) dan untuk boxes dipanggil dari library pytesseract yang telah di panggil sebelumnya sebagai file header.
pada "for b in boxes" adalah perintah untuk membentuk kotak serta formatnya seperti lebar kotak,panjang kotak, tinggi kotak dan ketebalan kotak dan setelah dipanggil maka gambar akan ditampilkan.
