```c++ :
#include <bits/stdc++.h>

using namespace std;

class SinhVien {
private:
    string ma_sv;
    string ho_ten;
    int tuoi;

public:
    SinhVien() : ma_sv(""), ho_ten(""), tuoi(0) {}

    virtual void nhap() {
        cout << "Nhap ma sv :  ";
        cin >> ma_sv;
        cout << "Ten: ";
        cin.ignore();
        getline(cin, ho_ten);
        cout << "Tuoi: ";
        cin >> tuoi;
    }

    virtual void in_thong_tin() {
        cout << "MSV: " << ma_sv << ", Ten: " << ho_ten << ", Tuoi: " << tuoi << endl;
    }

    void setMsv(string ma_sv) {
        this->ma_sv = ma_sv;
    }

    string getMaSV()  {
        return ma_sv;
    }

    void setTen(string ho_ten) {
        this->ho_ten = ho_ten;
    }

    string getHoTen()  {
        return ho_ten;
    }

    void setTuoi(int tuoi) {
        this->tuoi = tuoi;
    }

    int getTuoi()  {
        return tuoi;
    }
};

class DiemTongKet : public SinhVien {
private:
    float mon_toan;
    float mon_ly;
    float mon_hoa;

public:
    DiemTongKet() : mon_toan(0), mon_ly(0), mon_hoa(0) {}

    void nhap() override {
        SinhVien::nhap();
        cout << "Nhap diem mon Toan: ";
        cin >> mon_toan;
        cout << "Nhap diem mon Ly: ";
        cin >> mon_ly;
        cout << "Nhap diem mon Hoa: ";
        cin >> mon_hoa;
    }

    void in_thong_tin() override {
        SinhVien::in_thong_tin();
        cout << "Diem Toan: " << mon_toan << ", Diem Ly: " << mon_ly << ", Diem Hoa: " << mon_hoa << endl;
    }

    float tinh_diem_trung_binh() {
        return (mon_toan + mon_ly + mon_hoa) / 3;
    }

    string xep_loai() {
        float diem_tb = tinh_diem_trung_binh();
        if (diem_tb >= 8) {
            return "Gioi";
        } else if (diem_tb >= 6.5) {
            return "Kha";
        } else if (diem_tb >= 5) {
            return "Trung binh";
        } else {
            return "Yeu";
        }
    }
};

int main() {
    vector<DiemTongKet> danh_sach_sinh_vien;
    int n;

    cout << "Nhap so sinh vien: ";
    cin >> n;
    for (int i = 0; i < n; i++) {
        cout << "Nhap thong tin sinh vien thu " << i + 1 << ":\n";
        DiemTongKet sv;
        sv.nhap();
        danh_sach_sinh_vien.push_back(sv);
    }
    cout << "\nDanh sach sinh vien co diem trung binh >= 8:\n";
    for (auto& sv : danh_sach_sinh_vien) {
        if (sv.tinh_diem_trung_binh() >= 8) {
            sv.in_thong_tin();
            cout << "Diem trung binh: " << sv.tinh_diem_trung_binh() << endl;
            cout << "Xep loai: " << sv.xep_loai() << endl << endl;
        }
    }
    int so_sinh_vien_kha = 0;
    for (auto& sv : danh_sach_sinh_vien) {
        if (sv.xep_loai() == "Kha") {
            so_sinh_vien_kha++;
        }
    }
    cout << "So sinh vien dat loai kha: " << so_sinh_vien_kha << endl;

    return 0;
}
```
