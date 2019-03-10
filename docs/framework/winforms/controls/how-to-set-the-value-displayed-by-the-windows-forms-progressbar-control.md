---
title: HOW TO：設定 Windows Form ProgressBar 控制項顯示的值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: a889d6e5cd40833353c1b294031621b7b289ac4d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715889"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>HOW TO：設定 Windows Form ProgressBar 控制項顯示的值
> [!IMPORTANT]
>  
  <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]可讓您幾種不同的方式，顯示指定的值內<xref:System.Windows.Forms.ProgressBar>控制項。 您選擇哪種方法將取決於手邊的工作或您要解決的問題。 下表顯示方法，您可以選擇。  
  
|方法|描述|  
|--------------|-----------------|  
|值設定<xref:System.Windows.Forms.ProgressBar>直接控制。|這種方法可用於工作： 您知道所需，例如從資料來源讀取記錄的測量項目總計。 此外，如果您只需要將值設定為一或兩次，這就是這麼簡單的方法。 最後，如果您需要減少顯示進度列的值時，才能使用此程序。|  
|增加<xref:System.Windows.Forms.ProgressBar>顯示由固定值。|當您要顯示的最小值和最大值，例如已耗用時間或在已知的總計已處理的檔案數目之間的簡單計數，則這個方法會很有用。|  
|增加<xref:System.Windows.Forms.ProgressBar>顯示值，而有所不同。|當您需要變更所顯示的值在不同的金額重試次數，則這個方法會很有用。 範例會顯示為一系列的檔案寫入磁碟時所耗用的硬碟空間量。|  
  
 若要設定顯示進度列的值最直接的方式是藉由設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。 做法是在設計階段或在執行階段。  
  
### <a name="to-set-the-progressbar-value-directly"></a>若要直接設定 ProgressBar 值  
  
1.  設定<xref:System.Windows.Forms.ProgressBar>控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。  
  
2.  在程式碼，將控制項的<xref:System.Windows.Forms.ProgressBar.Value%2A>您已建立的最小和最大值之間的整數值的屬性。  
  
    > [!NOTE]
    >  如果您設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性所建立的界限之外<xref:System.Windows.Forms.ProgressBar.Minimum%2A>並<xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性，控制項就會擲回<xref:System.ArgumentException>例外狀況。  
  
     下列程式碼範例說明如何設定<xref:System.Windows.Forms.ProgressBar>直接值。 程式碼會從資料來源讀取記錄，並更新進度列和標籤，每次讀取資料記錄。 這個範例需要您的表單具有<xref:System.Windows.Forms.Label>控制<xref:System.Windows.Forms.ProgressBar>控制項，以及呼叫的資料列的資料表`CustomerRow`具有`FirstName`和`LastName`欄位。  
  
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
  
     如果您要顯示固定的間隔來進行的進度，您可以設定值，並接著呼叫的方法，會增加<xref:System.Windows.Forms.ProgressBar>該間隔的控制項的值。 這是適用於計時器和其他案例，您不整體的百分比測量進度的位置。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>若要固定值增加，進度列  
  
1.  設定<xref:System.Windows.Forms.ProgressBar>控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。  
  
2.  將控制項的<xref:System.Windows.Forms.ProgressBar.Step%2A>屬性設為整數，代表量增加的進度列的顯示值。  
  
3.  呼叫<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>方法來變更顯示設定的值<xref:System.Windows.Forms.ProgressBar.Step%2A>屬性。  
  
     下列程式碼範例說明一個進度列可以列印文件的維護，請在複製作業中的檔案數目。  
  
     在下列範例中，每個檔案讀入記憶體中，進度列和標籤會更新以反映讀取的檔案總數。 這個範例需要您的表單具有<xref:System.Windows.Forms.Label>控制項和<xref:System.Windows.Forms.ProgressBar>控制項。  
  
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
  
     最後，您可以增加，因此每次增加是唯一的數量，進度列所顯示的值。 當您所追蹤的一系列的唯一作業，例如不同大小的檔案寫入硬碟，或以整體的百分比測量進度，這非常有用。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>若要以動態的值增加，進度列  
  
1.  設定<xref:System.Windows.Forms.ProgressBar>控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。  
  
2.  呼叫<xref:System.Windows.Forms.ProgressBar.Increment%2A>方法，以變更您指定的整數所顯示的值。  
  
     下列程式碼範例說明如何複製作業期間已使用多少磁碟空間計算進度列。  
  
     在下列範例中，在每個檔案寫入硬碟中，進度列和標籤會更新以反映 可用的硬碟空間量。 這個範例需要您的表單具有<xref:System.Windows.Forms.Label>控制項和<xref:System.Windows.Forms.ProgressBar>控制項。  
  
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
