# pbl-project

#20250B131지현우/메인화면

mport os
import time

#계산기로직(더하기,빼기,곱하기,나누기)

def clear_screen():
    os.system('cls' if os.name == 'nt' else 'clear')

def print_banner():
    print("=================================")
    print("     계산기      ")
    print("=================================")
    print("  1. 더하기  (+)")
    print("  2. 빼기    (-)")
    print("  3. 곱하기  (*)")
    print("  4. 나누기  (/)")
    print("  Q. 종료하기")
    print("=================================")

def main():
    while True:
        clear_screen()
        print_banner()

        choice = input(">> 메뉴를 선택하세요: ").strip().upper()

        if choice == 'Q':
            print("프로그램을 종료합니다.")
            break

        if choice not in ['1', '2', '3', '4']:
            print("잘못된 입력입니다. 다시 선택해주세요.")
            time.sleep(1)
            continue

        try:
            num1 = float(input("첫 번째 숫자를 입력하세요: "))
            num2 = float(input("두 번째 숫자를 입력하세요: "))
        except ValueError:
            print("오류: 숫자로만 입력해야 합니다!")
            time.sleep(2)
            continue

        result = 0
        operator = ""

        if choice == '1':
            result = add(num1, num2)
            operator = "+"
        elif choice == '2':
            result = sub(num1, num2)
            operator = "-"
        elif choice == '3':
            result = mul(num1, num2)
            operator = "*"
        elif choice == '4':
            result = div(num1, num2)
            operator = "/"
            if result is None:
                print("오류: 0으로 나눌 수 없습니다.")
                input("엔터를 누르면 메뉴로 돌아갑니다...")
                continue

        print(f"\n[결과] {num1} {operator} {num2} = {result}")
        print("---------------------------------")
        input("엔터를 누르면 메뉴로 돌아갑니다...")

if __name__ == "__main__":
    main()

///
    
