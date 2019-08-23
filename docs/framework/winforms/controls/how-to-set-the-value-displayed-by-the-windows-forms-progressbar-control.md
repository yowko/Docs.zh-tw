---
title: 作法：設定 Windows Forms ProgressBar 控制項顯示的值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 2e0134206ba3ebdce35f5374cbad575e34483d58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956086"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>作法：設定 Windows Forms ProgressBar 控制項顯示的值
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 .NET Framework 提供幾種不同的<xref:System.Windows.Forms.ProgressBar>方式, 讓您在控制項中顯示指定的值。 您選擇的方法取決於手邊的工作或您要解決的問題。 下表顯示您可以選擇的方法。  
  
|方法|描述|  
|--------------|-----------------|  
|直接設定<xref:System.Windows.Forms.ProgressBar>控制項的值。|如果您知道將牽涉到的專案總數 (例如從資料來源讀取記錄), 這種方法就很有用。 此外, 如果您只需要設定一次或兩次的值, 這就是簡單的方法。 最後, 如果您需要減少進度列所顯示的值, 請使用此程式。|  
|以固定值增加顯示。<xref:System.Windows.Forms.ProgressBar>|當您要顯示介於最小值和最大值之間的簡單計數 (例如已耗用時間或已從已知總計處理的檔案數目) 時, 這個方法很有用。|  
|以不同的值來增加顯示。<xref:System.Windows.Forms.ProgressBar>|當您需要將顯示的值變更為不同數量的次數時, 這個方法很有用。 其中一個範例會顯示將一系列檔案寫入磁片時所耗用的硬碟空間量。|  
  
 若要設定進度列所顯示的值, 最直接的方式是設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。 這可以在設計階段或執行時間執行。  
  
### <a name="to-set-the-progressbar-value-directly"></a>若要直接設定 ProgressBar 值  
  
1. 設定控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。 <xref:System.Windows.Forms.ProgressBar>  
  
2. 在程式碼中, 將控制項<xref:System.Windows.Forms.ProgressBar.Value%2A>的屬性設定為您所建立之最小值和最大值之間的整數值。  
  
    > [!NOTE]
    > 如果您將<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性設定在<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性所建立的界限之外, 控制項<xref:System.ArgumentException>就會擲回例外狀況。  
  
     下列程式碼範例說明如何直接設定<xref:System.Windows.Forms.ProgressBar>值。 程式碼會從資料來源讀取記錄, 並在每次讀取資料記錄時更新進度列和標籤。 這個範例要求您的表單具有<xref:System.Windows.Forms.Label>控制項<xref:System.Windows.Forms.ProgressBar> 、控制項, 以及具有`FirstName`和`LastName`欄位的資料列`CustomerRow`的資料表。  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     如果您要顯示以固定間隔繼續進行的進度, 您可以設定值, 然後呼叫方法, 依該間隔增加<xref:System.Windows.Forms.ProgressBar>控制項的值。 這適用于不是以整體百分比測量進度的計時器和其他案例。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>以固定值增加進度列  
  
1. 設定控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。 <xref:System.Windows.Forms.ProgressBar>  
  
2. 將控制項的<xref:System.Windows.Forms.ProgressBar.Step%2A>屬性設定為整數, 代表要增加進度列顯示值的數量。  
  
3. 呼叫方法, 以變更<xref:System.Windows.Forms.ProgressBar.Step%2A>屬性中設定的數量所顯示的值。 <xref:System.Windows.Forms.ProgressBar.PerformStep%2A>  
  
     下列程式碼範例說明進度列可以如何在複製作業中維護檔案的計數。  
  
     在下列範例中, 當每個檔案讀入記憶體時, 進度列和標籤會更新, 以反映讀取的檔案總數。 此範例會要求您的表單<xref:System.Windows.Forms.Label>具有控制項<xref:System.Windows.Forms.ProgressBar>和控制項。  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     最後, 您可以增加進度列所顯示的值, 讓每個增加都是唯一的金額。 當您要追蹤一系列獨特的作業 (例如將不同大小的檔案寫入硬碟), 或以整體百分比測量進度時, 這會很有用。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>以動態值增加進度列  
  
1. 設定控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。 <xref:System.Windows.Forms.ProgressBar>  
  
2. <xref:System.Windows.Forms.ProgressBar.Increment%2A>呼叫方法, 以變更您指定的整數所顯示的值。  
  
     下列程式碼範例說明在複製作業期間, 進度列可以如何計算已使用的磁碟空間量。  
  
     在下列範例中, 當每個檔案寫入硬碟時, 會更新進度列和標籤以反映可用的硬碟空間量。 此範例會要求您的表單<xref:System.Windows.Forms.Label>具有控制項<xref:System.Windows.Forms.ProgressBar>和控制項。  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [ProgressBar 控制項概觀](progressbar-control-overview-windows-forms.md)
- [ProgressBar 控制項](progressbar-control-windows-forms.md)
