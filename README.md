#include <iostream>
#include <string>
#include <sstream>
#include <bitset>

std::string decimalParaHexadecimal(int decimal) {
    std::stringstream ss;
    ss << std::hex << std::uppercase << decimal;
    return ss.str();
}

std::string decimalParaBinario(int decimal) {
    std::string binario;
    if (decimal == 0) return "0";
    while (decimal > 0) {
        binario = (decimal % 2 == 0 ? "0" : "1") + binario;
        decimal /= 2;
    }
    return binario;
}

int main() {
    int decimal;
    std::cout << "Digite um numero decimal: ";
    std::cin >> decimal;

    if (decimal < 0) {
        std::cerr << "Erro: este programa so aceita numeros inteiros nao negativos.\n";
        return 1;
    }

    std::string binario = decimalParaBinario(decimal);
    std::string hexadecimal = decimalParaHexadecimal(decimal);

    std::cout << "Binário: " << binario << std::endl;
    std::cout << "Hexadecimal: " << hexadecimal << std::endl;

    return 0;
}



#include <iostream>
#include <string>
#include <cmath>
#include <sstream>
#include <iomanip>

using namespace std;

int binarioParaDecimal(const string& binario) {
    int decimal = 0;
    int tamanho = binario.length();
    for (int i = 0; i < tamanho; ++i) {
        if (binario[tamanho - 1 - i] == '1') {
            decimal += pow(2, i);
        } else if (binario[tamanho - 1 - i] != '0') {
            cerr << "Erro: entrada não é um número binário válido.\n";
            exit(1);
        }
    }
    return decimal;
}

string decimalParaHexadecimal(int decimal) {
    stringstream ss;
    ss << hex << uppercase << decimal;
    return ss.str();
}

int main() {
    string binario;
    cout << "Digite um numero binario: ";
    cin >> binario;

    int decimal = binarioParaDecimal(binario);
    string hexadecimal = decimalParaHexadecimal(decimal);

    cout << "Decimal: " << decimal << endl;
    cout << "Hexadecimal: " << hexadecimal << endl;

    return 0;
}



#include <iostream>
#include <string>
#include <sstream>
#include <bitset>
#include <cctype>

std::string limparHexadecimal(const std::string& hex) {
    if (hex.size() >= 2 && hex[0] == '0' && (hex[1] == 'x' || hex[1] == 'X')) {
        return hex.substr(2);
    }
    return hex;
}

int hexadecimalParaDecimal(const std::string& hex) {
    int decimal;
    std::stringstream ss;
    ss << std::hex << hex;
    ss >> decimal;
    if (ss.fail()) {
        std::cerr << "Erro: entrada hexadecimal inválida.\n";
        exit(1);
    }
    return decimal;
}

std::string decimalParaBinario(int decimal) {
    if (decimal == 0) return "0";
    std::string binario;
    while (decimal > 0) {
        binario = (decimal % 2 == 0 ? "0" : "1") + binario;
        decimal /= 2;
    }
    return binario;
}

int main() {
    std::string entradaHex;
    std::cout << "Digite um numero hexadecimal: ";
    std::cin >> entradaHex;

    std::string hexLimpo = limparHexadecimal(entradaHex);

    int decimal = hexadecimalParaDecimal(hexLimpo);

    std::string binario = decimalParaBinario(decimal);

    std::cout << "Decimal: " << decimal << std::endl;
    std::cout << "Binário: " << binario << std::endl;

    return 0;
}
