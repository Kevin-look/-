#include<iostream>
#include<string>

using namespace std;
//系统中需要实现的功能
//添加联系人
//显示，删除，查找，修改，清空，退出

///联系人结构体
struct Preson
{
    string name;
    string sex;//1男2女
    int age;
    string phone;
    string address;

};
//通讯录结构体
struct Addressbooks
{
    struct Preson personArray[100];//储存联系人的结构体数组,personArray[0]代表第一个联系人结构体
    int size;//储存通讯录中人员的个数
};


//菜单封装
void ShowMenu()
{  
    cout << "**********************" << endl;
    cout << "*****1.添加联系人*****" << endl;
    cout << "*****2.显示联系人*****" << endl;
    cout << "*****3.删除联系人*****" << endl;
    cout << "*****4.查找联系人*****" << endl;
    cout << "*****5.修改联系人*****" << endl;
    cout << "*****6.清空联系人*****" << endl;
    cout << "*****0.退出通讯录*****" << endl;
    cout << "**********************" << endl;
}

//添加联系人
void addPerson(struct Addressbooks* abs) {
    //通讯录是否满了
    if (abs->size >= 100)
    {
        cout << "通讯录已经满了。" << endl;
        return;
    }
    //开始添加
    string name;
    cout << "请输入姓名：" << endl;
    cin >> name;
    abs->personArray[abs->size].name = name;
    
    /*string sex;
    cout << "请输入性别：" << endl;
    cin >> sex;
    abs->personArray[abs->size].sex = sex;

    int age;
    cout << "请输入年龄：" << endl;
    cin >> age;
    abs->personArray[abs->size].age = age;

    string phone;
    cout << "请输入电话：" << endl;
    cin >> phone;
    abs->personArray[abs->size].phone = phone;


    string address;
    cout << "请输入地址：" << endl;
    cin >> address;
    abs->personArray[abs->size].address = address;*/

    abs->size++;
    
    system("pause");
    cout << "请按任意键继续. . ." << endl;
    system("cls");//清屏操作
    cout << "添加成功" << "\n" << "此时通讯录有" << abs->size << "个人" << endl;
    
}



///显示联系人
void showPerson(struct Addressbooks* abs) 
{
    if (abs->size == 0) {
        cout<<"当前记录为空" << endl;
    }

    for (int i = 0; i < abs->size; i++) {
        cout << "这是第" << i + 1 << "个联系人的信息：" << endl;
        cout << "  姓名：" << abs->personArray[i].name << endl;
        cout << "  性别：" << abs->personArray[i].sex<< endl;
        cout << "  年龄：" << abs->personArray[i].age  << endl;
        cout << "  电话：" << abs->personArray[i]. phone<< endl;
        cout << "  地址：" << abs->personArray[i]. address<< endl;
    }
    printf("\n\n");
    system("pause");
}


//删除联系人
//要遍历查找联系人的名字

//查找一个人是否存在
bool isExist(struct Addressbooks* abs,string name) 
{
    for (int i = 0; i < abs->size; i++) {
        if (abs->personArray[i].name == name) {
            return i;//第i+1个

        }
    }
    return -1;

}

//删除联系人
void deletePerson(Addressbooks* abs) {
    cout << "请输入你要删除的联系人" << endl;
    string name;
    cin >> name;
    
    //没查到-1；查到了ret！=-1；
    int ret=isExist(abs, name);
    if (ret != -1) {
        //开始删除
        //数据前移
        for (int i = ret; i < abs->size-1; i++) 
        {
            abs->personArray[i] = abs->personArray[i + 1];
        }
        abs->size--;
        cout << "删除成功" << endl;
        cout << "现在有" << abs->size << "个联系人"<<endl;

    }
    else {
        cout << "查无此人" << endl;
    }

}



int main() {

    //创建通讯录结构体变量
    struct Addressbooks abs;
    ///当前人员个数
    abs.size = 0;


    int select = 0;//用户的输入
    while (1)
    {
        ShowMenu();
        cin >> select;
        switch (select) {
        case 1:addPerson(&abs);
            break;

        case 2:showPerson(&abs);
            break;

        case 3: {
        
            deletePerson(&abs);


            break;
        }
        case 4:
            break;

        case 5:
            break;

        case 6:
            break;

        case 0:
            cout << "欢迎下次使用！" << endl;
            system("pause");
            return 0;
            break;


        default:
            break;
        }
    }

    

    system("pause");
    return 0;
}# -
