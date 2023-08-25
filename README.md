# justlogin
//beauti strick;
#include <iostream>
#include<fstream>
#include<string>
#include <random>
using namespace std;
void
call_functon ()
{
  string username, password;
  cout << " username " << endl;
  cin >> username;
  cout << " password " << endl;
  cin >> password;
  ofstream outfile ("f.txt", ios::app);
  // outfile.open("file_student" , ios::app);
  outfile << username << " " << password;
  outfile.close ();
  cout << " account created" << endl;

}

int
login ()
{
  cout << " fill ths capcha" << endl;
  random_device jexa;
  mt19937 hey (jexa ());
  vector < int >v;
  vector < char >c;
  for (char x = 'a'; x < 'z'; x++)
    {
      c.push_back (x);
    }
  std::uniform_real_distribution <> dis (0.0, 1.0);
  for (int i = 0; i < 10; i++)
    {

      if (dis (hey) < 0.3)
	{
	  v.push_back (i);
	  cout << i << c[i];

	}
	
    }
    cout<<endl;;
  for (int i = 0; i < v.size (); i++)
    {
      int x;
      cin >> x;
      if (x != v[i])
	{
	  //  cout<<" worng capttch "<<endl;
	  return -1;
	}

    }


  cout << " for login give username and password " << endl;
  string username, password;
  cin >> username >> password;
  ifstream infile ("f.txt");
  string storedusername, storedpassword;
  while (infile >> storedusername >> storedpassword)
    {
      if (storedusername == username and storedpassword == password)
	{
	  infile.close();
	  return 1;
	}
    }
  infile.close();
  return 0;

}

int
main()
{
  int coice;
  do
    {
      cout << " coice " << endl;
      cout << "1.creat_aacount " << endl;
      cout << "2.login" << endl;
      cout << "3.exit" << endl;
      cin >> coice;
      switch (coice)
	{

	case 1:
	  call_functon ();
	  break;
	case 2:
	  if (login () == 1)
	    {
	      cout << " login " << endl;

	    }
	  else if (login () == 0)
	    {
	      cout << " no data found" << endl;
	    }
	  else
	    {
	      cout << " worng capttch" << endl;;
	    }
	  break;

	case 3:
	  cout << "exit";
	  break;
	default:

	  cout << " chal palate , masti nahi " << endl;
	  return 0;
	}
    }
  while (coice != 2);



  return 0;
}
