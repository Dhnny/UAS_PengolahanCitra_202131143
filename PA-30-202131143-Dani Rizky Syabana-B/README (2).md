#Project Akhir pengolahan citra "word segmentation"
Project kali ini adalah bagaimana cara melakukan segmentasi pada sebuah kata berupa nama lengkap sendiri dan dilakukan sesi foto dengan device masing-masing.

#Import Library
Pada library project kali ini menggunakan library OpenCV yang berfungsi sebagai mengolah dan mengekstrak informasi pada sebuah citra dan selanjutnya adalah library tesseract yang berfungsi sebagai support untuk melakukan word recognition pada word segmentation kali ini

#memanggil gambar dan memanggil library tesseract
pytesseract.pytesseract.tesseract_cmd = 'C:\Program Files\Tesseract-OCR\tesseract.exe'

img = cv2.imread('Dani2.jpeg')

img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB) print(pytesseract.image_to_boxes(img))

cv2.imshow('Result',img)

cv2.waitKey(0)

pada inputan di atas adalah memanggil tesseract pada program file di pc dan juga memanggil gambar yang ingin dilakukan segmentasi dan untuk "img = cv2.cvtColor(img,cv2.COLOR_BGR2RGB) print(pytesseract.image_to_boxes(img))" merupakan perintah untuk mengkonversi gambar menjadi RGB dan juga melakukan print kotak segementasi dengan pytesseract

#Memanggil variabel image shape
hImg,wImg,_ = img.shape

inputan di atas adalah perintah memasukkan variabel gambar yang nantinya akan digunakan untuk mengubah bentuk citra yang dimana hImg adalah tinggi gambar dan wImg adalah lebar gambar.

#memanggil boxes
boxes = pytesseract.image_to_boxes(img)

for b in boxes.splitlines():

perintah di atas merupakan perintah untuk memanggil box atau kotak segmentasi yang berfungsi sebagai pemisah antar kata 

#print kotak
print(b) 
b = b.split(' ')
print(b)
x,y,w,h = int(b[1]),int(b[2]),int(b[3]),int(b[3])
cv2.rectangle(img, (x,hImg-y), (w,hImg-h),(0, 0, 255),2)

inputan kali ini adalah inputan untuk melakukan pencetakkan pada kotak yang dimana b disini menjadi variabel kotaknya dan b = b.split(' ') sebagai perintah untuk melakukan pemisahan kata pada citra 

"x,y,w,h = int(b[1]),int(b[2]),int(b[3]),int(b[3])"
nilai-nilai x, y, w, dan h diberikan melalui mengubah elemen-elemen array b yang merupakan argumen fungsi.
Elemen-elemen array tersebut menggunakan tipe data string, dan dengan menggunakan fungsi int(), sehingga mengonversinya menjadi tipe data integer.

"cv2.rectangle(img, (x,hImg-y), (w,hImg-h),(0, 0, 255),2)"
Fungsi kotak dari pustaka OpenCV yang digunakan untuk menggambar persegi panjang pada gambar.
Parameter pertama, img, adalah gambar di mana persegi panjang akan digambar.
Parameter kedua dan ketiga adalah titik awal dan titik akhir persegi panjang. Titik awal (x, hImg - y) dan titik akhir (w, hImg - h).
Koordinat (x, y) menunjukkan sudut kiri atas persegi panjang, sedangkan (w, h) menunjukkan sudut kanan bawah persegi panjang.
Parameter keempat, (0, 0, 255), adalah nilai warna dalam format BGR (Blue, Green, Red). Dalam kasus ini, persegi panjang akan berwarna merah.
Parameter kelima, 2, adalah ketebalan garis persegi panjang yang akan digambar.

#Mencetak gambar yang telah di segmentasi
cv2.imshow('Result',img)

cv2.waitKey(0)