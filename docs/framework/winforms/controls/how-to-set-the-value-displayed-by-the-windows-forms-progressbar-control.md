---
title: 如何：設定 Windows Form ProgressBar 控制項顯示的值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 66093cacea4f76ab65af40658f03c03ce7560f0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540114"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>如何：設定 Windows Form ProgressBar 控制項顯示的值
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供數個不同的方式來顯示給定的值內<xref:System.Windows.Forms.ProgressBar>控制項。 您選擇哪種方法將取決於手邊的工作或已解決的問題。 下表顯示方法，您可以選擇。  
  
|方法|描述|  
|--------------|-----------------|  
|值設定<xref:System.Windows.Forms.ProgressBar>直接控制。|這種方法可用於工作就會涉及，例如從資料來源中讀取記錄的測量項目總計。 此外，如果您只需要將值設定為一或兩次，這是簡單的方法。 最後，如果您需要減少進度列所顯示的值時，才能使用這個程序。|  
|增加<xref:System.Windows.Forms.ProgressBar>顯示由固定值。|顯示簡單計數之間的最小值和最大值，例如已耗用時間或在已知的總計已處理的檔案數目時，這個方法很有用。|  
|增加<xref:System.Windows.Forms.ProgressBar>顯示的值，而有所不同。|當您需要變更顯示的值不同的金額重試次數時，這個方法很有用。 範例會顯示一系列的檔案寫入磁碟時所耗用的硬碟空間量。|  
  
 若要設定進度列所顯示的值最直接的方式是藉由設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。 作法是在設計階段或執行階段。  
  
### <a name="to-set-the-progressbar-value-directly"></a>若要直接設定 ProgressBar 的值  
  
1.  設定<xref:System.Windows.Forms.ProgressBar>控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。  
  
2.  程式碼中，將控制項的<xref:System.Windows.Forms.ProgressBar.Value%2A>已建立的最小和最大值之間的整數值的屬性。  
  
    > [!NOTE]
    >  如果您設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性所建立的界限之外<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性、 控制項就會擲回<xref:System.ArgumentException>例外狀況。  
  
     下列程式碼範例說明如何設定<xref:System.Windows.Forms.ProgressBar>直接值。 程式碼會從資料來源中讀取記錄，並每次讀取資料記錄會更新進度列和標籤。 這個範例需要您的表單具有<xref:System.Windows.Forms.Label>控制項，<xref:System.Windows.Forms.ProgressBar>控制項，以及資料表資料列呼叫`CustomerRow`與`FirstName`和`LastName`欄位。  
  
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
  
     如果您要顯示固定的間隔來進行的進度，您可以設定值，並接著呼叫的方法，會增加<xref:System.Windows.Forms.ProgressBar>該間隔的控制項的值。 這是適用於計時器和其他案例，您不以整體的百分比測量進度的位置。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>若要固定值增加進度列  
  
1.  設定<xref:System.Windows.Forms.ProgressBar>控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。  
  
2.  將控制項的<xref:System.Windows.Forms.ProgressBar.Step%2A>屬性為整數，代表量增加進度列顯示值。  
  
3.  呼叫<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>方法，以變更顯示設定的值<xref:System.Windows.Forms.ProgressBar.Step%2A>屬性。  
  
     下列程式碼範例說明如何將進度列可以維護的複製作業中的檔案計數。  
  
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
  
     最後，您可以增加顯示進度列，因此每次增加數量都是唯一的值。 當您為追蹤的一系列的唯一作業，例如不同大小的檔案寫入硬碟，或以整體的百分比測量進度，這非常有用。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>若要動態值增加進度列  
  
1.  設定<xref:System.Windows.Forms.ProgressBar>控制項的<xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。  
  
2.  呼叫<xref:System.Windows.Forms.ProgressBar.Increment%2A>方法，以變更顯示您指定的整數的值。  
  
     下列程式碼範例說明如何複製作業期間已使用多少磁碟空間計算進度列。  
  
     在下列範例中，在每個檔案寫入硬碟，進度列和標籤會更新以反映的可用硬碟空間量。 這個範例需要您的表單具有<xref:System.Windows.Forms.Label>控制項和<xref:System.Windows.Forms.ProgressBar>控制項。  
  
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
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [ProgressBar 控制項概觀](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [ProgressBar 控制項](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
