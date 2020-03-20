---
title: 設置進度列控制項顯示的值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: d295079a96ca19a4e4c98e113a3f3051c6403182
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141807"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a><span data-ttu-id="a6129-102">如何：設定 Windows Form ProgressBar 控制項顯示的值</span><span class="sxs-lookup"><span data-stu-id="a6129-102">How to: Set the Value Displayed by the Windows Forms ProgressBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="a6129-103"><xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="a6129-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="a6129-104">.NET 框架為您提供了幾種在<xref:System.Windows.Forms.ProgressBar>控制項中顯示給定值的不同方法。</span><span class="sxs-lookup"><span data-stu-id="a6129-104">The .NET Framework gives you several different ways to display a given value within the <xref:System.Windows.Forms.ProgressBar> control.</span></span> <span data-ttu-id="a6129-105">您選擇的方法將取決於手頭的任務或正在解決的問題。</span><span class="sxs-lookup"><span data-stu-id="a6129-105">Which approach you choose will depend on the task at hand or the problem you are solving.</span></span> <span data-ttu-id="a6129-106">下表顯示了您可以選擇的方法。</span><span class="sxs-lookup"><span data-stu-id="a6129-106">The following table shows the approaches you can choose.</span></span>  
  
|<span data-ttu-id="a6129-107">方法</span><span class="sxs-lookup"><span data-stu-id="a6129-107">Approach</span></span>|<span data-ttu-id="a6129-108">描述</span><span class="sxs-lookup"><span data-stu-id="a6129-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a6129-109">直接設置<xref:System.Windows.Forms.ProgressBar>控制項的值。</span><span class="sxs-lookup"><span data-stu-id="a6129-109">Set the value of the <xref:System.Windows.Forms.ProgressBar> control directly.</span></span>|<span data-ttu-id="a6129-110">此方法對於知道將涉及的項總數（例如從資料來源讀取記錄）的任務非常有用。</span><span class="sxs-lookup"><span data-stu-id="a6129-110">This approach is useful for tasks where you know the total of the item measured that will be involved, such as reading records from a data source.</span></span> <span data-ttu-id="a6129-111">此外，如果您只需要設置該值一次或兩次，這是一種簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="a6129-111">Additionally, if you only need to set the value once or twice, this is an easy way to do it.</span></span> <span data-ttu-id="a6129-112">最後，如果需要減小進度條顯示的值，請使用此過程。</span><span class="sxs-lookup"><span data-stu-id="a6129-112">Finally, use this process if you need to decrease the value displayed by the progress bar.</span></span>|  
|<span data-ttu-id="a6129-113">增加<xref:System.Windows.Forms.ProgressBar>顯示值。</span><span class="sxs-lookup"><span data-stu-id="a6129-113">Increase the <xref:System.Windows.Forms.ProgressBar> display by a fixed value.</span></span>|<span data-ttu-id="a6129-114">當您在最小值和最大值之間顯示簡單計數（如經過時間或從已知總數中處理的檔數）時，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="a6129-114">This approach is useful when you are displaying a simple count between the minimum and maximum, such as elapsed time or the number of files that have been processed out of a known total.</span></span>|  
|<span data-ttu-id="a6129-115">增加<xref:System.Windows.Forms.ProgressBar>顯示量，該值各不相同。</span><span class="sxs-lookup"><span data-stu-id="a6129-115">Increase the <xref:System.Windows.Forms.ProgressBar> display by a value that varies.</span></span>|<span data-ttu-id="a6129-116">當您需要以不同數量多次更改顯示的值時，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="a6129-116">This approach is useful when you need to change the displayed value a number of times in different amounts.</span></span> <span data-ttu-id="a6129-117">例如，顯示在將一系列檔寫入磁片時消耗的硬碟空間量。</span><span class="sxs-lookup"><span data-stu-id="a6129-117">An example would be showing the amount of hard-disk space being consumed while writing a series of files to the disk.</span></span>|  
  
 <span data-ttu-id="a6129-118">設置進度條顯示的值的最直接方法是設置<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a6129-118">The most direct way to set the value displayed by a progress bar is by setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="a6129-119">這可以在設計時或運行時完成。</span><span class="sxs-lookup"><span data-stu-id="a6129-119">This can be done either at design time or at run time.</span></span>  
  
### <a name="to-set-the-progressbar-value-directly"></a><span data-ttu-id="a6129-120">直接設置進度列值</span><span class="sxs-lookup"><span data-stu-id="a6129-120">To set the ProgressBar value directly</span></span>  
  
1. <span data-ttu-id="a6129-121">設置<xref:System.Windows.Forms.ProgressBar>控制項和<xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。</span><span class="sxs-lookup"><span data-stu-id="a6129-121">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="a6129-122">在代碼中，將控制項的屬性<xref:System.Windows.Forms.ProgressBar.Value%2A>設置為已建立的最小值和最大值之間的整數值。</span><span class="sxs-lookup"><span data-stu-id="a6129-122">In code, set the control's <xref:System.Windows.Forms.ProgressBar.Value%2A> property to an integer value between the minimum and maximum values you have established.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a6129-123">如果將<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性設置為 和<xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性建立的邊界之外，則控制項將引發異常。 <xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="a6129-123">If you set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property outside the boundaries established by the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties, the control throws an <xref:System.ArgumentException> exception.</span></span>  
  
     <span data-ttu-id="a6129-124">以下代碼示例說明了如何直接設置<xref:System.Windows.Forms.ProgressBar>值。</span><span class="sxs-lookup"><span data-stu-id="a6129-124">The following code example illustrates how to set the <xref:System.Windows.Forms.ProgressBar> value directly.</span></span> <span data-ttu-id="a6129-125">代碼從資料來源讀取記錄，並在每次讀取資料記錄時更新進度列和標籤。</span><span class="sxs-lookup"><span data-stu-id="a6129-125">The code reads records from a data source and updates the progress bar and label every time a data record is read.</span></span> <span data-ttu-id="a6129-126">此示例要求表單<xref:System.Windows.Forms.Label>具有控制項、<xref:System.Windows.Forms.ProgressBar>控制項和具有名為`CustomerRow`和`FirstName`欄位`LastName`的行的資料表。</span><span class="sxs-lookup"><span data-stu-id="a6129-126">This example requires that your form has a <xref:System.Windows.Forms.Label> control, a <xref:System.Windows.Forms.ProgressBar> control, and a data table with a row called `CustomerRow` with `FirstName` and `LastName` fields.</span></span>  
  
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
  
     如果要顯示按固定間隔繼續的進度，則可以設置該值，然後調用一個方法，該方法按該間隔增加<xref:System.Windows.Forms.ProgressBar>控制項的值。 <span data-ttu-id="a6129-128">這對於計時器和其他方案非常有用，因為計時器和其他方案沒有將進度作為整個百分比來衡量。</span><span class="sxs-lookup"><span data-stu-id="a6129-128">This is useful for timers and other scenarios where you are not measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a><span data-ttu-id="a6129-129">將進度條增加一個固定值</span><span class="sxs-lookup"><span data-stu-id="a6129-129">To increase the progress bar by a fixed value</span></span>  
  
1. <span data-ttu-id="a6129-130">設置<xref:System.Windows.Forms.ProgressBar>控制項和<xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。</span><span class="sxs-lookup"><span data-stu-id="a6129-130">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="a6129-131">將控制項的屬性<xref:System.Windows.Forms.ProgressBar.Step%2A>設置為表示金額的整數，以增加進度條的顯示值。</span><span class="sxs-lookup"><span data-stu-id="a6129-131">Set the control's <xref:System.Windows.Forms.ProgressBar.Step%2A> property to an integer representing the amount to increase the progress bar's displayed value.</span></span>  
  
3. <span data-ttu-id="a6129-132">調用<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>方法以更改<xref:System.Windows.Forms.ProgressBar.Step%2A>屬性中設置的金額顯示的值。</span><span class="sxs-lookup"><span data-stu-id="a6129-132">Call the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method to change the value displayed by the amount set in the <xref:System.Windows.Forms.ProgressBar.Step%2A> property.</span></span>  
  
     <span data-ttu-id="a6129-133">以下代碼示例說明了進度列如何維護複製操作中檔的計數。</span><span class="sxs-lookup"><span data-stu-id="a6129-133">The following code example illustrates how a progress bar can maintain a count of the files in a copy operation.</span></span>  
  
     <span data-ttu-id="a6129-134">在下面的示例中，當每個檔讀入記憶體時，進度列和標籤將更新以反映讀取的總檔。</span><span class="sxs-lookup"><span data-stu-id="a6129-134">In the following example, as each file is read into memory, the progress bar and label are updated to reflect the total files read.</span></span> <span data-ttu-id="a6129-135">此示例要求表單具有控制項<xref:System.Windows.Forms.Label>和<xref:System.Windows.Forms.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="a6129-135">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
     最後，您可以增加進度條顯示的值，以便每次增加都是唯一的量。 <span data-ttu-id="a6129-137">當您跟蹤一系列獨特的操作（例如將不同大小的檔寫入硬碟或測量進度作為整個百分比）時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="a6129-137">This is useful when you are keeping track of a series of unique operations, such as writing files of different sizes to a hard disk, or measuring progress as a percentage of the whole.</span></span>  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a><span data-ttu-id="a6129-138">按動態值增加進度條</span><span class="sxs-lookup"><span data-stu-id="a6129-138">To increase the progress bar by a dynamic value</span></span>  
  
1. <span data-ttu-id="a6129-139">設置<xref:System.Windows.Forms.ProgressBar>控制項和<xref:System.Windows.Forms.ProgressBar.Minimum%2A><xref:System.Windows.Forms.ProgressBar.Maximum%2A>值。</span><span class="sxs-lookup"><span data-stu-id="a6129-139">Set the <xref:System.Windows.Forms.ProgressBar> control's <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> values.</span></span>  
  
2. <span data-ttu-id="a6129-140">調用<xref:System.Windows.Forms.ProgressBar.Increment%2A>方法以更改指定整數顯示的值。</span><span class="sxs-lookup"><span data-stu-id="a6129-140">Call the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method to change the value displayed by an integer you specify.</span></span>  
  
     <span data-ttu-id="a6129-141">以下代碼示例說明了進度條如何計算複製操作期間使用的磁碟空間量。</span><span class="sxs-lookup"><span data-stu-id="a6129-141">The following code example illustrates how a progress bar can calculate how much disk space has been used during a copy operation.</span></span>  
  
     <span data-ttu-id="a6129-142">在下面的示例中，當每個檔寫入硬碟時，進度列和標籤將更新以反映可用的硬碟空間量。</span><span class="sxs-lookup"><span data-stu-id="a6129-142">In the following example, as each file is written to the hard disk, the progress bar and label are updated to reflect the amount of hard-disk space available.</span></span> <span data-ttu-id="a6129-143">此示例要求表單具有控制項<xref:System.Windows.Forms.Label>和<xref:System.Windows.Forms.ProgressBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="a6129-143">This example requires that your form has a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.ProgressBar> control.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6129-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6129-144">See also</span></span>

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [<span data-ttu-id="a6129-145">ProgressBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a6129-145">ProgressBar Control Overview</span></span>](progressbar-control-overview-windows-forms.md)
- [<span data-ttu-id="a6129-146">ProgressBar 控制項</span><span class="sxs-lookup"><span data-stu-id="a6129-146">ProgressBar Control</span></span>](progressbar-control-windows-forms.md)
