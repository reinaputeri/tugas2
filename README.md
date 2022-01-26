# tugas2
//Tugas 2
//Round Robin Schedulling

//Nama : Reina Puteri Ramadhani
//NIM : 18320039

#include<iostream>
using namespace std;
 
//input data
int main()
{
    //data proses
    cout << "Masukkan jumlah proses : "
    cin >> jumlah_proses;
    int proses[] = { 0, 1, 2, 3, 4, 5};
    int n = sizeof proses / sizeof proses[0];
 
    //data waktu kedatangan
    int data_wd[] = {0, 50, 130, 190, 210, 350};
 
    // nilai quantum
    int quantum = 100;
    return 0;
}

void waktuTunggu(int proses[], int n, int wd[],
            int wt[], int quantum)
{
    
    // waktu kedatangan
    int data_wd[n];
    for (int i = 0 ; i < n ; i++)
        data_wd[i] = wd[i];
 
    int waktu = 0; //waktu sekarang
 
    while (1)
    {
        bool selesai = true;
 
        for (int i = 0 ; i < n; i++)
        {
            if (data_wd[i] > 0)
            {
                selesai = false; 
                if (data_wd[i] > quantum)
                {
                    waktu += quantum;
                    data_wd[i] -= quantum;
                }
 
                else
                {
                    waktu = waktu + data_wd[i];
                    wt[i] = waktu - wd[i];
                    data_wd[i] = 0;
                }
            }
        }
 
        if (selesai == true)
        break;
    }
}
void totalWaktu(int proses[], int n, int wd[], int quantum)
{
    int wt[n], total_wt = 0;
    
//output
    cout << "Proses "<< " Waktu Kedatangan "
        << " Waktu Tunggu ";
 
    //Perhitungan total waktu tunggu
    for (int i=0; i<n; i++)
    {
        total_wt = total_wt + wt[i];
        cout << " " << i+1 << "\t\t" << wt[i] <<"\t ";
    }
    cout << "Total waktu tunggu = "
        << (float)total_wt;
}
