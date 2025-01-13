```c++ :
#include <bits/stdc++.h>
using namespace std;

class ThietBi {
private:
    string ten;
    string nhaSanXuat;
    int namSanXuat;
public:
    ThietBi() : ten(""), nhaSanXuat(""), namSanXuat(0) {}
    void setTen(string t) { ten = t; }
    string getTen() { return ten; }
    void setNam(int n) { namSanXuat = n; }
    int getNam() { return namSanXuat; }
    void setNhaSanXuat(string nsx) { nhaSanXuat = nsx; }
	string getNhaSanXuat() { return nhaSanXuat; }
    virtual void nhap() {
        cout << "Nhap ten thiet bi: ";
        getline(cin, ten);
        cout << "Nhap nha san xuat: ";
        getline(cin, nhaSanXuat);
        cout << "Nhap nam san xuat: ";
        cin >> namSanXuat;
        cin.ignore();
    }
    virtual void xuat()  {
        cout << "Ten: " << ten << ", Nha san xuat: " << nhaSanXuat << ", Nam san xuat: " << namSanXuat;
    }
    virtual ~ThietBi() {}
};
class DieuHoa : public ThietBi {
private: float congSuat;
public:
    DieuHoa() : congSuat(0.0) {}
    void nhap() override {
        ThietBi::nhap();
        cout << "Nhap cong suat (kW): ";
        cin >> congSuat;
        cin.ignore();
    }
    void xuat() override {
        ThietBi::xuat();
        cout << ", Cong suat: " << congSuat << " kW";
    }
};

class MayTinh : public ThietBi {
private:
    int ram;
    string cpu;

public:
    MayTinh() : ram(0), cpu("") {}

    void nhap() override {
        ThietBi::nhap();
        cout << "Nhap RAM (GB): ";
        cin >> ram;
        cin.ignore();
        cout << "Nhap CPU: ";
        getline(cin, cpu);
    }

    void xuat() override {
        ThietBi::xuat();
        cout << ", RAM: " << ram << " GB, CPU: " << cpu;
    }
};

class PhongHoc {
private:
    string maPhong;
    string tenPhong;
    vector<DieuHoa> dsDieuHoa;
    vector<MayTinh> dsMayTinh;

public:
    void nhap() {
        cout << "Nhap ma phong: ";
        getline(cin, maPhong);
        cout << "Nhap ten phong: ";
        getline(cin, tenPhong);
    }

    void themDieuHoa() {
        DieuHoa dh;
        dh.nhap();
        dsDieuHoa.push_back(dh);
    }

    void themMayTinh() {
        MayTinh mt;
        mt.nhap();
        dsMayTinh.push_back(mt);
    }

    void hienThi() {
        cout << "Ma phong: " << maPhong << ", Ten phong: " << tenPhong << endl;
        cout << "Danh sach dieu hoa:\n";
        for (size_t i = 0; i < dsDieuHoa.size(); ++i) {
            cout << "  Dieu hoa " << i + 1 << ": ";
            dsDieuHoa[i].xuat();
            cout << endl;
        }

        cout << "Danh sach may tinh:\n";
        for (size_t i = 0; i < dsMayTinh.size(); ++i) {
            cout << "  May tinh " << i + 1 << ": ";
            dsMayTinh[i].xuat();
            cout << endl;
        }
    }
};

int main() {
    PhongHoc phongHoc;
    phongHoc.nhap();

    int luaChon;
    do {
        cout << "\n1. Them dieu hoa";
        cout << "\n2. Them may tinh";
        cout << "\n3. Hien thi thong tin phong";
        cout << "\n0. Thoat";
        cout << "\nNhap lua chon: ";
        cin >> luaChon;
        cin.ignore();

        switch (luaChon) {
        case 1:
            phongHoc.themDieuHoa();
            break;
        case 2:
            phongHoc.themMayTinh();
            break;
        case 3:
            phongHoc.hienThi();
            break;
        case 0:
            cout << "Thoat chuong trinh." << endl;
            break;
        default:
            cout << "Lua chon khong hop le." << endl;
        }
    } while (luaChon != 0);

    return 0;
}
```
