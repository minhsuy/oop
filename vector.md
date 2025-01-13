```c++ :
#include <iostream>
#include <cmath>
using namespace std;

class Vector {
private:
    double x;
    double y;

public:
	Vector() {
		this -> x = 0 ;
		this -> y = 0 ;
	}
   Vector(double x , double y) {
   		this -> x = x ;
   	 	this -> y =y ;
   }
   void setX(double x) {
   	this -> x = x ;
   }
   double getX()  {
   		return x ;
   }
    void setY(double y) {
        this->y = y;
    }
    double getY()  {
        return y;
    }
	Vector cong(Vector v) {
		return Vector(this->x + v.getX() , this->y + v.getY()) ;
	}
    Vector tru( Vector v)  {
        return Vector(this->x - v.getX(), this->y - v.getY());
    }


    friend double nhan( Vector v1,  Vector v2);

	Vector nhanVoiSo(double k) {
		return Vector(this -> x * k , this -> y * k ) ;
	}
    void hienThi()  {
        cout << "(" << x << ", " << y << ")" << endl;
    }
};

double nhan( Vector v1,  Vector v2) {
	return v1.getX() * v2.getX() + v1.getY() * v2.getY();
}

int main() {

    Vector v1(3, 4);
    Vector v2(1, 2);

    cout << "Vector v1: ";
    v1.hienThi();

    cout << "Vector v2: ";
    v2.hienThi();


	Vector v3 = v1.cong(v2) ;
    cout << "Vector v1 + v2: ";
    v3.hienThi();


    Vector v4 = v1.tru(v2);
    cout << "Vector v1 - v2: ";
    v4.hienThi();

    double kq = nhan(v1, v2);
    cout << "Tich vo huong (v1 . v2): " << kq << endl;

	 double k = 2;
    Vector v5 = v1.nhanVoiSo(k);
    cout << "Vector v1 nhan vs K " << k << ": ";
    v5.hienThi();
    return 0;
}
```
