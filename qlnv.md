```c++ :
#include <bits/stdc++.h>
using namespace std;

class NhanSu {
protected:
    string maNhanVien;
    string hoTen;
    string gioiTinh;
    int namSinh;

public:
     virtual void nhap() {
        cout << "Nhap ma nhan vien: ";
        cin >> maNhanVien;
        cin.ignore();
        cout << "Nhap ho ten: ";
        getline(cin, hoTen);
        cout << "Nhap gioi tinh : ";
        cin >> gioiTinh;
        cout << "Nhap nam sinh: ";
        cin >> namSinh;
    }

    virtual void in() {
        cout << "Ma nhan vien: " << maNhanVien << endl;
        cout << "Ho ten: " << hoTen << endl;
        cout << "Gioi tinh: " << gioiTinh << endl;
        cout << "Nam sinh: " << namSinh << endl;
    }


  bool kiemTraNghiHuu() {
  	int tuoi = 2024 - this->namSinh;
  	if((tuoi >= 60 && (this->gioiTinh == "Nam" ||  this->gioiTinh == "nam" || this->gioiTinh == "1")) || (tuoi >= 55 && (this->gioiTinh == "Nu" || this->gioiTinh == "nu" || this->gioiTinh == "2"))) return true ;
  	return false ;
  }
};

class CanBo : public NhanSu {
private:
    string chuyenMon;
    double heSoLuong;
    double phuCap;
    string trinhDo;

public:
    void nhap() override {
        NhanSu::nhap();
        cout << "Nhap chuyen mon: ";
        cin.ignore();
        getline(cin, chuyenMon);
        cout << "Nhap he so luong: ";
        cin >> heSoLuong;
        cout << "Nhap phu cap: ";
        cin >> phuCap;
        cout << "Nhap trinh do: ";
        cin.ignore();
        getline(cin, trinhDo);
    }

    void in() override {
        NhanSu::in();
        cout << "Chuyen mon: " << chuyenMon << endl;
        cout << "He so luong: " << heSoLuong << endl;
        cout << "Phu cap: " << phuCap << endl;
        cout << "Trinh do: " << trinhDo << endl;
    }

   double tinhLuong() {
   	return this->heSoLuong * 2000 + this->phuCap ;
   }
};

class CongNhan : public NhanSu {
private:
    long long mucLuong;
    int ngayCong;

public:
    void nhap() override {
        NhanSu::nhap();
        cout << "Nhap muc luong: ";
        cin >> mucLuong;
        cout << "Nhap so ngay cong: ";
        cin >> ngayCong;
    }

    void in() override {
        NhanSu::in();
        cout << "Muc luong: " << mucLuong << endl;
        cout << "So ngay cong: " << ngayCong << endl;
    }


    double tinhLuong()  {
        return mucLuong * ngayCong;
    }
};

int main() {

    CanBo canBo;
    CongNhan congNhan;


    cout << "Nhap thong tin can bo:" << endl;
    canBo.nhap();


    cout << "Nhap thong tin cong nhan:" << endl;
    congNhan.nhap();


    cout << "Thong tin can bo:" << endl;
    canBo.in();
    cout << "Luong: " << canBo.tinhLuong() << endl;
    cout << (canBo.kiemTraNghiHuu() ? "Can bo da du tuoi nghi huu" : "Can bo chua den tuoi nghi huu") << endl;

    cout << "Thong tin cong nhan:" << endl;
    congNhan.in();
    cout << "Luong: " << congNhan.tinhLuong() << endl;
    cout << (congNhan.kiemTraNghiHuu() ? "Cong nhan da den tuoi nghi huu" : "Cong nhan chua den tuoi nghi huu") << endl;

    return 0;
}
```
