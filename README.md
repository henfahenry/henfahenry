import os

# 帳號和密碼
username = "HENFA0310"
password = "1234598765"

# 登入函數
def login():
    input_username = input("請輸入帳號：")
    input_password = input("請輸入密碼：")
    if input_username == username and input_password == password:
        print("登入成功！")
        return True
    else:
        print("帳號或密碼錯誤！")
        return False

# 上傳檔案函數
def upload_file():
    if not os.path.exists("uploads"):
        os.makedirs("uploads")
    file_name = input("請輸入要上傳的檔案名稱：")
    with open(f"uploads/{file_name}", "w") as file:
        file_content = input("請輸入檔案內容：")
        file.write(file_content)
    print("檔案已成功上傳！")

# 下載檔案函數
def download_file():
    file_name = input("請輸入要下載的檔案名稱：")
    try:
        with open(f"uploads/{file_name}", "r") as file:
            file_content = file.read()
            print("檔案內容：")
            print(file_content)
    except FileNotFoundError:
        print("檔案不存在！")

# 主程式
def main():
    logged_in = False
    while not logged_in:
        logged_in = login()
    
    while True:
        print("\n1. 上傳檔案")
        print("2. 下載檔案")
        print("3. 登出")
        choice = input("請選擇操作：")
        
        if choice == "1":
            upload_file()
        elif choice == "2":
            download_file()
        elif choice == "3":
            print("已登出。")
            break
        else:
            print("請輸入有效選項！")

# 執行主程式
if __name__ == "__main__":
    main()
