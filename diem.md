```c++ :
#include <bits/stdc++.h>
using namespace std;
#define PI 3.14

class Diem {
private:
    float x, y;

public:
    Diem() : x(0.0), y(0.0) {}
    Diem(float hoanhDo, float tungDo) : x(hoanhDo), y(tungDo) {}
    void setHoanhDo(float x) {
        this->x = x;
    }
    void setTungDo(float y) {
        this->y = y;
    }
    float getHoanhDo()  {
        return x;
    }
    float getTungDo()  {
        return y;
    }
    ~Diem() {
        cout << "Ham huy diem" << endl;
    }
};

class Hinh : public Diem {
public:
	virtual void Nhap() { }
    virtual float dienTich() {
    	return 0 ;
	};
    virtual void xuatDienTich() {
        cout << "Dien tich: " << dienTich() << endl;
    }
};

class HinhTron : public Hinh {
private:
    Diem tam;
    float R;
public:
    void Nhap() override {
        cout << "Nhap ban kinh: ";
        cin >> R;
    }
    float dienTich() override {
        return PI * R * R;
    }
    void xuatDienTich() override {
        cout << "Dien tich hinh tron: " << dienTich() << endl;
    }
};

class HinhVuong : public Hinh {
private:
    float c;
public:
    void Nhap() override {
        cout << "Nhap canh: ";
        cin >> c;
    }
    void xuat() {
        cout << "Day la hinh vuong\n";
    }
    float dienTich() override {
        return c * c;
    }
    void xuatDienTich() override {
        cout << "Dien tich hinh vuong: " << dienTich() << endl;
    }
};

int main() {
	int  n ;
	cout << "Nhap so luong :" ;
	cin >> n ;
    vector<Hinh*> danhSachHinh;
    for (int i = 0; i < n; ++i) {
    	cout << "Nhap canh cho hinh chu nhat : " ;
        HinhVuong* hinhVuong = new HinhVuong();
        hinhVuong->Nhap();
        danhSachHinh.push_back(hinhVuong);
    }
    for (int i = 0; i < n; ++i) {
    	cout << "Nhap ban kinh cho hinh tron : " ;
        HinhTron* hinhTron = new HinhTron();
        hinhTron->Nhap();
        danhSachHinh.push_back(hinhTron);
    }
    for (auto hinh : danhSachHinh) {
        hinh->xuatDienTich();
    }
    return 0;
}
```
