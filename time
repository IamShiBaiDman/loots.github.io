#include <stdio.h>
#include <string.h>
#include <math.h>

typedef struct student {
	char name[20];
	char class[10];
	char number[10];
	int timestart;
	int timeend;
}Student,*PTR;
Student No[10] = { //学生档案结构体
	{ "Null","Null","Null    ",1220,2018 },
	{ "孙笑川","A班","22050113",1020,2324 },
	{ "蔡徐坤","B班","21000000",140,2310 },
	{ "肖战","B班","20000000",2310,240 },
	{ "stu4","D班","19000000",200,300 },
	{ "/","Null","Null",0,0 }
};
PTR ptr;
int peopleNumbre = 0;
float Price = 0.0;

//刷新档案人数
int PeopleNumbre() {
	int i=0;
	ptr = No;
	while (*ptr->name != '/') {
		i++;
		ptr++;
	}
	peopleNumbre = i;
	return i;
}

//字符串转换数字
int strConversionNumber(char* str) {//输入字符串返回数字
	int number = 0, i = 0;
	int lenght = 0;
	lenght = (int)strlen(str);
	for (i = 0; i < lenght; i++) {
		number += (int)(str[i] - 48) * (int)pow(10, lenght - i - 1);
		//printf("%d\n", number);
	}
	return number;
}

//学生信息添加
datainput() {
	int i=0;
	char Timestart[5] = "0", Timeend[5] = "0";
	PeopleNumbre();
	ptr = No;
	printf("——————————————————————————————————\n");
	printf("输入格式：\n");
	printf("姓名：Null\n");
	printf("班级 学号 开始时间 结束时间\nNull Null 0\t   0\n");
	printf("输入'/'结束添加\n");
	ptr += peopleNumbre;
	do {
		printf("姓名：");
		scanf_s("%s", ptr->name, 19);
		if (*ptr->name == '/') break;
		printf("班级 学号 上机时间 下机时间\n");
		scanf_s("%s%s%s%s", ptr->class, 19, ptr->number, 9, &Timestart, 5, &Timeend, 5);
		ptr->timestart = strConversionNumber(Timestart);
		ptr->timeend = strConversionNumber(Timeend);
		while(strlen(ptr->number) != 8) {
			printf("学号必须为8位！\n请重新输入:");
			scanf_s("%s", ptr->number, 9);
		}
		while (ptr->timestart < 100 || ptr->timestart>2359) {
			printf("上机时间格式错误范围！\n请重新输入:");
			scanf_s("%s", &Timestart, 5);
			ptr->timestart = strConversionNumber(Timestart);
		}
		while (ptr->timeend < 100 || ptr->timeend>2359) {
			printf("下机时间格式错误范围！\n请重新输入:");
			scanf_s("%s", &Timeend, 5);
			ptr->timeend = strConversionNumber(Timeend);
		}
		printf("\007\033[32m添加成功！\033[0m\n——————————————————————————————————\n输入'/'结束添加\n");
		ptr++;
		i++;
	} while (i!=10);
	printf("\007\033[32m保存成功！\033[0m\n");
	printf("——————————————————————————————————\n");
}

//修改档案
Seting() {
	int i = 0;
	char stop[4] = "0";
	char Name[20] = "0", Class[10] = "0", Number[10] = "0";
	char Timestart[5] = "0", Timeend[5] = "0";
	int timestart = 0, timeend = 0;
	while (1) {
		ptr = No;
		eixt:
		printf("请输入需要编辑的档案序号(输入'/'返回)\n");
		scanf_s("%s", &stop, 3);
		if (stop[0] == '/')break;
		i =(int) stop[0] - 48;
		if (i > peopleNumbre || i < 1) goto eixt;//输入的值只能是1~9的数字和'/'
		printf("————————————————————————————————————————————————————————————————————————\n");
		printf("已选择编号 '%d'\n", i);
		ptr += i-1;
		printf("姓名\t班级\t学号\t\t上机时间\t下机时间\n");
		printf("%s\t%s\t%s\t%d：%d\t\t%d：%d\n", ptr->name, ptr->class, ptr->number,
			ptr->timestart / 100, ptr->timestart % 100, ptr->timeend / 100, ptr->timeend % 100);
		printf("————————————————————————————————————————————————————————————————————————\n");
		printf("姓名 班级 学号 上机时间 下机时间(输入'/' x<100 or x>2359(时间)不修改项)\n");// 是三项都输入'/'表示不修改
		printf("姓名：");
		scanf_s("%s", &Name, 19);
		printf("班级：");
		scanf_s("%s", &Class, 9);
		printf("学号：");
		scanf_s("%s", &Number, 9);
		while (strlen(Number) != 8) {//学号应该为8位数字！
			printf("学号应该为8位数字！\n请重新输入:");
			scanf_s("%s", Number, 9);
		}
		printf("上机时间：");							//这里会检测输入的数据类型，strconversionnumber()函数解决了int timestart输入了字符串会崩溃的Bug
		scanf_s("%s", &Timestart, 5);					//将输入的存入char Timestart，在传输给strconversionnumber(),返回一个字符串数字对应的十进制数字
		timestart = strConversionNumber(Timestart);		//timeend同理
		printf("下机时间：");
		scanf_s("%s", &Timeend, 5);
		timeend = strConversionNumber(Timeend);
		if (Name[0] != '/')
			strcpy_s(ptr->name, strlen(Name) + 1, Name);
		if (Class[0] != '/')
			strcpy_s(ptr->class, strlen(Class) + 1, Class);
		if (Number[0] != '/')
			strcpy_s(ptr->number, strlen(Number) + 1, Number);
		if (timestart >= 100 && timestart <= 2459)
			ptr->timestart = timestart;
		if (timeend >= 100 && timeend <= 2459)
			ptr->timeend = timeend;
		printf("————————————————————————————————————————————————————————————————\n");
		printf("\007\033[32m编辑成功！\033[0m\n当前档案为：\n");
		printf("姓名\t班级\t学号\t\t上机时间\t下机时间\n");
		printf("%s\t%s\t%s\t%d：%d\t\t%d：%d\n", ptr->name, ptr->class, ptr->number,
			ptr->timestart / 100, ptr->timestart % 100, ptr->timeend / 100, ptr->timeend % 100);
		printf("————————————————————————————————————————————————————————————————\n");
	}
	printf("\007\033[32m保存成功！\033[0m\n");
}

//删除
Delet() {
	int i, j = 0;
	char stop[4] = "0";
	char Name[20] = "0", Class[10] = "0", Number[10] = "0";
	while (1) {
		PeopleNumbre();
	eixt:
		printf("选择删除的档案序号('/'返回):");
		scanf_s("%s", &stop, 3);
		if (stop[0] == '/')break;//'/'返回
		i = (int)stop[0] - 48;
		if (i > peopleNumbre) goto eixt;//输入的值只能是1~9的数字和'/'
		printf("已选择编号 '%d'\n", i);
		printf("1.确认 2.取消\n");
		scanf_s("%d", &j);
		if (j == 2)goto eixt;
		else if (j == 1) {
			for (; i <= peopleNumbre; i++) {
				ptr = No;
				ptr += i - 1;
				strcpy_s((ptr++)->name, strlen(ptr->name) + 1, ptr->name);
				ptr = No;
				ptr += i - 1;
				strcpy_s((ptr++)->class, strlen(ptr->class) + 1, ptr->class);
				ptr = No;
				ptr += i - 1;
				strcpy_s((ptr++)->number, strlen(ptr->number) + 1, ptr->number);
				ptr += i - 1;
				(ptr++)->timestart = ptr->timestart;
				ptr += i - 1;
				(ptr++)->timeend = ptr->timeend;
			}
		}
		else goto eixt;
		printf("\007\033[31m删除成功\033[0m\n");
		printf("——————————————————————————————————\n");
	}
	printf("\007\033[32m保存成功！\033[0m\n");
}

//收费计算
jisuan(float price) {
	int hour, min, TotalTime, i = 0;
	hour = min = TotalTime = 0;
	ptr = No;
	printf("\033[32m所有学生档案信息和当前累计收费：\033[0m\n");
	while (*ptr->name != '/') {
		printf("————————————————————————————————————————————————————————————————\n");
		printf("序号\t姓名\t班级\t学号\t\t上机时间\t下机时间\n");
		printf("%d\t%s\t%s\t%s\t%d：%d\t\t%d：%d\n", i + 1, ptr->name, ptr->class, ptr->number,
			ptr->timestart / 100, ptr->timestart % 100, ptr->timeend / 100, ptr->timeend % 100);
		//当上机时间在一天之内
		if (ptr->timestart <= ptr->timeend) {
			hour = (ptr->timeend - ptr->timestart) / 100;
			min = (ptr->timeend - ptr->timestart) % 100;
			if (ptr->timeend % 100 - ptr->timestart % 100 < 0) {//结束时间分钟小于开始时间分钟
				min = (ptr->timeend % 100 + 60) - ptr->timestart % 100;
			}
		}
		//当上机时间到了第二天
		else if (ptr->timestart > ptr->timeend){
			hour = (24 - ptr->timestart / 100) + ptr->timeend/ 100;
			min = ptr->timeend % 100 - ptr->timestart % 100;
			if (ptr->timeend % 100 - ptr->timestart % 100 < 0) {//结束时间分钟小于开始时间分钟
				hour--;
			}
				min = (ptr->timeend % 100 + 60) - ptr->timestart % 100;
		}
		TotalTime = hour * 60 + min;
		printf("总共上机时间：%d小时%d分钟(%d分钟)\n",hour,min,TotalTime);
		printf("结算：%.3f元\n", TotalTime * price);
		ptr++;
		i++;
	}
	printf("\n");
}

//查询
search() {
	int i, null = 0;
	int temp[3] = {0};
	char searchdata[20] = "0";
	PeopleNumbre();//重新获取学生档案数量
	while (1) {
		printf("输入查询学生档案相关的信息(姓名，班级，学号，返回'/')：\n");
		scanf_s("%s", &searchdata, 19);
		if (searchdata[0] == '/')break;
		null = 0;
		ptr = No;
		for (i = 0; i <= peopleNumbre; i++) {
			temp[0] = strcmp(searchdata, ptr->name);
			temp[1] = strcmp(searchdata, ptr->class);
			temp[2] = strcmp(searchdata, ptr->number);
			if ((temp[0] == 0 || temp[1] == 0 || temp[2] == 0) && *ptr->name != '/') {
				printf("序号\t姓名\t班级\t学号\t\t上机时间\t下机时间\n");
				printf("%d\t%s\t%s\t%s\t", i + 1, ptr->name, ptr->class, ptr->number);
				printf("%d：%d\t\t%d：%d\n", ptr->timestart / 100, ptr->timestart % 100, ptr->timeend / 100, ptr->timeend % 100);
				null++;
			}
			ptr++;
		}
		if (null == 0) {
			printf("没有搜索到该生的任何信息！请重新搜索\n");
		}
	}
}

//编辑档案
xiugai() {
	int i;
	printf("————————————————————————\n");
	printf("1.添加\t注意：\n2.修改\t修改时间为12:10\n3.删除\t输入格式为1210\n4.返回\t时间修改范围为100~2359\n");
	printf("————————————————————————\n");
	scanf_s("%d", &i);
	switch (i) {
	case 1:datainput(); break;
	case 2:Seting(); break;
	case 3:Delet(); break;
	case 4:break;
	default:break;
	}
}

setprice() {
	float price = 0;
	printf("当前网费单价为：%.3f元/分钟\n", Price);
	printf("输入的金额(小于等于0不修改)：");
	scanf_s("%f", &price);
	if (price > 0) {
		Price = price;
		printf("\033[32m修改成功\033[0m！\n");
	}
	else
		printf("\033[33m修改失败\033[0m！\n");
}

//显示
Display() {
	int i = 0, page = 1;
	char str[4] = "0";
	printf("————————————————————————————————————————————————————————————————\n");
	printf("序号\t姓名\t班级\t学号\t\t上机时间\t下机时间\n");
	while (1) {
		PeopleNumbre();
		ptr = No;
		i = (page - 1) * 3;
		ptr += i;
		printf("————————————————————————————————————————————————————————————————\n");
		for (; i < page * 3; i++) {//三个档案一页
			if (*ptr->name == '/')break;
			printf("%d\t%s\t%s\t%s\t%d：%d\t\t%d：%d\n", i + 1, ptr->name, ptr->class, ptr->number,
				ptr->timestart / 100, ptr->timestart % 100, ptr->timeend / 100, ptr->timeend % 100);
			ptr++;
		}
		printf("————————————————————————————————————————————————————————————————\n");
		printf("页码：\t%d/%d\t'/'返回 'p'结算 's'搜索 'a'添加 'd'删除 'o'修改\n", page, peopleNumbre % 3 != 0 ? peopleNumbre / 3 + 1 : peopleNumbre / 3);
		printf("————————————————————————————————————————————————————————————————\n");
	eixt:
		printf("选择：");
		scanf_s("%s", &str, 3);
		if (str[0] == '/') break;//'/'返回
		switch (str[0]) {
		case 'a':datainput(); break;
		case 'd':Delet(); break;
		case 'o':Seting(); break;
		case 's':search(); break;
		case 'p':jisuan(Price); break;
		default:break;
		}
		page = (int)str[0] - 48;
		if (page > (peopleNumbre % 3 != 0 ? peopleNumbre / 3 + 1 : peopleNumbre / 3) || page < 0) goto eixt;
	}
}

//系统控制
systemcomputer() {
	char str[4] = "0";
	int temp = 0, i = 0;
	printf("———————————\033[32m欢迎使用机房收费管理系统\033[0m———————————\n");
	while (1) {
		if (i != 0)
			printf("——————————————————————————————————————————————\n");
		printf("1.浏览学生档案列表\t当前上机价格：%.3f\n", Price);
		printf("2.计算学生上机收费\n");
		printf("3.搜索学生档案\n");
		printf("4.编辑学生档案\n");
		printf("5.修改上机价格\n");
		printf("6.退出系统\n");
		printf("——————————————————————————————————————————————\n");
	eixt:
		printf("选择：");
		scanf_s("%s", &str, 3);
		i = (int)str[0] - 48;
		if (i > 6) goto eixt;
		switch (i) {
		case 1:Display(); break;
		case 2:jisuan(Price); break;
		case 3:search(); break;
		case 4:xiugai(); break;
		case 5:setprice(); break;
		default:break;
		}
		if (i == 6)break;
	}
}

//主函数
main() {
	Price = 0.07f;
	PeopleNumbre();//档案初始化，统计系统档案人数
	systemcomputer();//主界面
	printf("\033[32m成功退出\033[0m！\n");
	return 0;

}
