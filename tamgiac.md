```c++ :
#include <iostream>
#include <cmath>
using namespace std;

// L?p TamGiac
class TamGiac {
protected:
    double Ax, Ay, Bx, By, Cx, Cy;

public:
    TamGiac(double ax, double ay, double bx, double by, double cx, double cy) : Ax(ax), Ay(ay), Bx(bx), By(by), Cx(cx), Cy(cy) {}
    double doDaiCanh(double x1, double y1, double x2, double y2) {
        return sqrt(pow(x1 - x2, 2) + pow(y1 - y2, 2));
    }
    virtual double chuVi() {
        double AB = doDaiCanh(Ax, Ay, Bx, By);
        double BC = doDaiCanh(Bx, By, Cx, Cy);
        double CA = doDaiCanh(Cx, Cy, Ax, Ay);
        return AB + BC + CA;
    }
    virtual double dienTich() {
        double AB = doDaiCanh(Ax, Ay, Bx, By);
        double BC = doDaiCanh(Bx, By, Cx, Cy);
        double CA = doDaiCanh(Cx, Cy, Ax, Ay);
        double p = chuVi() / 2;
        return sqrt(p * (p - AB) * (p - BC) * (p - CA));
    }

    virtual void hienThi() {
        cout << "A(" << Ax << ", " << Ay << "), "
             << "B(" << Bx << ", " << By << "), "
             << "C(" << Cx << ", " << Cy << ")" << endl;
    }
};

class TamGiacCan : public TamGiac {
public:
    TamGiacCan(double ax, double ay, double bx, double by, double cx, double cy)
        : TamGiac(ax, ay, bx, by, cx, cy) {
        if (!kiemTraCan()) {
            cout << ("Tam giac nay khong phai tam giac can");
        }
    }

    bool kiemTraCan() {
        double AB = doDaiCanh(Ax, Ay, Bx, By);
        double BC = doDaiCanh(Bx, By, Cx, Cy);
        double CA = doDaiCanh(Cx, Cy, Ax, Ay);
        return (AB == BC || AB == CA || BC == CA);
    }
};

int main() {
        TamGiac M(0, 0, 4, 0, 0, 3);
        M.hienThi();
        cout << "Chu vi: " << M.chuVi() << endl;
        cout << "Dien tich: " << M.dienTich() << endl;

        TamGiacCan MC(0, 0, 4, 0, 2, 3);
        MC.hienThi();
        cout << "Chu vi: " << MC.chuVi() << endl;
        cout << "Dien tich: " << MC.dienTich() << endl;

    return 0;
}
```
