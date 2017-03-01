# -1
#include <iostream>
#include <windows.h>
using std::cin;
using std::cout;
#include <fstream>
using std::fstream;
#include <cmath>
#define epsilon 0.00000000001
double get_discriminant( double &a, double &b, double &c ) {
return b*b - 4 * a*c;
}
void output( double &a, double &b, double &c ) {
double x1 = 0.0;
double x2 = 0.0;
double discr = 0.0;
fstream out;
out.open( "roots.txt", std::fstream::out );
cout << "Коэффициенты квадратного уравнения:\n";
cout << "a: " << a << ", b: " << b << ", c: " << c << "\n";
discr = get_discriminant( a, b, c );
cout << "Дискриминант: " << discr << "\n";
if( discr < 0.0 ) {
cout << "Вещественных корней нет\n";
out << "No roots";
} else if( abs(discr) < epsilon ) {
cout << x1 = x2 = " << -b / ( 2 * a );
out << "x1 = " << x1 << "\n";
out << "x2 = " << x2 << "\n";
} else {
x1 = ( -b - sqrt( discr ) ) / ( 2 * a );
x2 = ( -b + sqrt( discr ) ) / ( 2 * a );
cout << " x1 = " << x1 << "\n";
cout << "x2 = " << x2 << "\n";
cout<<"Два вещественных корня\n";
out << "x1 = " << x1 << "\n";
out << "x2 = " << x2 << "\n";
out<<"Два вещественных корня\n";
}
out.close();
}
bool input( double &number ) {
char str[ 1024 ];
fgets( str, 1024, stdin );
for( size_t i = 0; i < strlen( str ) - 1; i++ ) {
if (((int)str[i]<48||(int)str[i]>57)&&str[i]!=','&&str[i]!='-') {
return false;
}
}
number = atof( str );
return true;
}
void input_abc( double &a, double &b, double &c ) {
cout << "Введите коэффициенты квадратного уравнения\n";
cout << "Для ввода десятичной запятой используйте ','\n";
do {
cout << "Введите коэффициент a: ";
}
while( !input( a ) || abs( a ) < epsilon );
do {
cout << "Введите коэффициент b: ";
}
while( !input( b ) );
do {
cout << "Введите коэффициент c: ";
}
while( !input( c ) );
output( a, b, c );
}
int main() {
setlocale( LC_ALL, "russian" );
double a = 0.0;
double b = 0.0;
double c = 0.0;
char menuChoice = 0;
do {
input_abc(a, b, c);
cout << "\nПовторить ввод? (Да - Нажмите на любую клавишу, Нет - 0):";
menuChoice = _getch();
cout << "\n";
} while (menuChoice != '0');
system( "pause" );
return EXIT_SUCCESS;
}
