#include <iostream>
#include <string>
using namespace std;

class Monster
{
private:
	int HP;
	string Type;
public:
	Monster(int Hallow = 100, string T = "default")
	{
		HP = Hallow;
		Type = T;
	}
	void fn()
	{
		cout << "HP:" << HP << endl;
		cout << "속성 : " << Type << endl;
	}
	virtual void Spawn() = 0;
};

class FlyMon : public Monster
{
private:
	int Altitude;
public:
	FlyMon(int Hallow, string T, int Al = 50) : Monster(Hallow, T)
	{
		Altitude = Al;
	}
	void Spawn()
	{
		cout << "적 출현" << endl;
		cout << "고도 : " << Altitude << endl;
		fn();
	}
};

class RunMon : public Monster
{
private:
	int Position;
public:
	RunMon(int Hallow, string T, int Pos = 100) : Monster(Hallow, T)
	{
		Position = Pos;
	}
	void Spawn()
	{
		cout << " 적 출현" << endl;
		cout << " 전방" << Position << "미터" << endl;
		fn();
	}
};

int main()
{
	Monster* A = new FlyMon(300, "Fire", 70);
	RunMon B(600, "ICE", 28);
	A->Spawn();
	B.Spawn();
	return 0;
}
