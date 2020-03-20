---
title: 如何：將資料繫結至 MaskedTextBox 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
- data binding [Windows Forms], MaskedTextBox control [Windows Forms]
- MaskedTextBox control [Windows Forms], binding data
ms.assetid: 34b29f07-e8df-48d4-b08b-53fcca524708
ms.openlocfilehash: 0cbb239e24b254c37c453486590185e934adf482
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142169"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="435eb-102">如何：將資料繫結至 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="435eb-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="435eb-103">您可以像綁定到任何其他<xref:System.Windows.Forms.MaskedTextBox>Windows 表單控制項一樣將資料繫結到控制項。</span><span class="sxs-lookup"><span data-stu-id="435eb-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="435eb-104">但是，如果資料庫中的資料格式與遮罩定義所需的格式不匹配，則需要重新格式化資料。</span><span class="sxs-lookup"><span data-stu-id="435eb-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="435eb-105">下面的過程演示如何使用<xref:System.Windows.Forms.Binding.Format><xref:System.Windows.Forms.Binding.Parse><xref:System.Windows.Forms.Binding>類 的 和 事件將單獨的電話號碼和電話分機資料庫欄位顯示為單個可編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="435eb-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="435eb-106">以下過程要求您有權訪問安裝了北風示例資料庫的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="435eb-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="435eb-107">將資料繫結到蒙版文字方塊控制項</span><span class="sxs-lookup"><span data-stu-id="435eb-107">To bind data to a MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="435eb-108">建立新的 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="435eb-108">Create a new Windows Forms project.</span></span>  
  
2. <span data-ttu-id="435eb-109">將兩<xref:System.Windows.Forms.TextBox>個控制項拖到表單上;命名它們`FirstName`和`LastName`。</span><span class="sxs-lookup"><span data-stu-id="435eb-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3. <span data-ttu-id="435eb-110">將<xref:System.Windows.Forms.MaskedTextBox>控制項拖到表單上;命名它`PhoneMask`。</span><span class="sxs-lookup"><span data-stu-id="435eb-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4. <span data-ttu-id="435eb-111">將<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>的屬性`PhoneMask`設置為`(000) 000-0000 x9999`。</span><span class="sxs-lookup"><span data-stu-id="435eb-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5. <span data-ttu-id="435eb-112">將以下命名空間導入添加到表單中。</span><span class="sxs-lookup"><span data-stu-id="435eb-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. <span data-ttu-id="435eb-113">按右鍵表單並選擇 **"查看代碼**"。</span><span class="sxs-lookup"><span data-stu-id="435eb-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="435eb-114">在此代碼放置在表單類的任意位置。</span><span class="sxs-lookup"><span data-stu-id="435eb-114">Place this code anywhere in your form class.</span></span>  
  
    ```csharp  
    Binding currentBinding, phoneBinding;  
    DataSet employeesTable = new DataSet();  
    SqlConnection sc;  
    SqlDataAdapter dataConnect;  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        DoMaskBinding();  
    }  
  
    private void DoMaskBinding()  
    {  
        try  
        {  
            sc = new SqlConnection("Data Source=CLIENTUE;Initial Catalog=NORTHWIND;Integrated Security=SSPI");  
            sc.Open();  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
  
        dataConnect = new SqlDataAdapter("SELECT * FROM Employees", sc);  
        dataConnect.Fill(employeesTable, "Employees");  
  
        // Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        // before adding them to the control - otherwise, we won't get a Format event on the
        // initial load.
        try  
        {  
            currentBinding = new Binding("Text", employeesTable, "Employees.FirstName");  
            firstName.DataBindings.Add(currentBinding);  
  
            currentBinding = new Binding("Text", employeesTable, "Employees.LastName");  
            lastName.DataBindings.Add(currentBinding);  
  
            phoneBinding =new Binding("Text", employeesTable, "Employees.HomePhone");  
            // We must add the event handlers before we bind, or the Format event will not get called  
            // for the first record.  
            phoneBinding.Format += new ConvertEventHandler(phoneBinding_Format);  
            phoneBinding.Parse += new ConvertEventHandler(phoneBinding_Parse);  
            phoneMask.DataBindings.Add(phoneBinding);  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
    }  
    ```  
  
    ```vb  
    Dim WithEvents CurrentBinding, PhoneBinding As Binding  
    Dim EmployeesTable As New DataSet()  
    Dim sc As SqlConnection  
    Dim DataConnect As SqlDataAdapter  
  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        DoMaskedBinding()  
    End Sub  
  
    Private Sub DoMaskedBinding()  
        Try  
            sc = New SqlConnection("Data Source=SERVERNAME;Initial Catalog=NORTHWIND;Integrated Security=SSPI")  
            sc.Open()  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Exit Sub  
        End Try  
  
        DataConnect = New SqlDataAdapter("SELECT * FROM Employees", sc)  
        DataConnect.Fill(EmployeesTable, "Employees")  
  
        ' Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        ' before adding them to the control - otherwise, we won't get a Format event on the
        ' initial load.  
        Try  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.FirstName")  
            firstName.DataBindings.Add(CurrentBinding)  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.LastName")  
            lastName.DataBindings.Add(CurrentBinding)  
            PhoneBinding = New Binding("Text", EmployeesTable, "Employees.HomePhone")  
            PhoneMask.DataBindings.Add(PhoneBinding)  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Application.Exit()  
        End Try  
    End Sub  
    ```  
  
7. <span data-ttu-id="435eb-115"><xref:System.Windows.Forms.Binding.Format>為 和<xref:System.Windows.Forms.Binding.Parse>事件添加事件處理常式，以合併`PhoneNumber`和`Extension`欄位與綁定<xref:System.Data.DataSet>的 欄位分離。</span><span class="sxs-lookup"><span data-stu-id="435eb-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
    ```csharp  
    private void phoneBinding_Format(Object sender, ConvertEventArgs e)  
    {  
        String ext;  
  
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        if (currentRow["Extension"] == null)
        {  
            ext = "";  
        } else
        {  
            ext = currentRow["Extension"].ToString();  
        }  
  
        e.Value = e.Value.ToString().Trim() + " x" + ext;  
    }  
  
    private void phoneBinding_Parse(Object sender, ConvertEventArgs e)  
    {  
        String phoneNumberAndExt = e.Value.ToString();  
  
        int extIndex = phoneNumberAndExt.IndexOf("x");  
        String ext = phoneNumberAndExt.Substring(extIndex).Trim();  
        String phoneNumber = phoneNumberAndExt.Substring(0, extIndex).Trim();  
  
        //Get the current binding object, and set the new extension manually.
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        // Remove the "x" from the extension.  
        currentRow["Extension"] = ext.Substring(1);  
  
        //Return the phone number.  
        e.Value = phoneNumber;  
    }  
    ```  
  
    ```vb  
    Private Sub PhoneBinding_Format(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Format  
        Dim Ext As String  
  
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        If (CurrentRow("Extension") Is Nothing) Then  
            Ext = ""  
        Else  
            Ext = CurrentRow("Extension").ToString()  
        End If  
  
        e.Value = e.Value.ToString().Trim() & " x" & Ext  
    End Sub  
  
    Private Sub PhoneBinding_Parse(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Parse  
        Dim PhoneNumberAndExt As String = e.Value.ToString()  
  
        Dim ExtIndex As Integer = PhoneNumberAndExt.IndexOf("x")  
        Dim Ext As String = PhoneNumberAndExt.Substring(ExtIndex).Trim()  
        Dim PhoneNumber As String = PhoneNumberAndExt.Substring(0, ExtIndex).Trim()  
  
        ' Get the current binding object, and set the new extension manually.
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        ' Remove the "x" from the extension.  
        CurrentRow("Extension") = CObj(Ext.Substring(1))  
  
        ' Return the phone number.  
        e.Value = PhoneNumber  
    End Sub  
    ```  
  
8. <span data-ttu-id="435eb-116">向表單<xref:System.Windows.Forms.Button>添加兩個控制項。</span><span class="sxs-lookup"><span data-stu-id="435eb-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="435eb-117">命名它們`previousButton`和`nextButton`。</span><span class="sxs-lookup"><span data-stu-id="435eb-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="435eb-118">按兩下每個按鈕以添加<xref:System.Windows.Forms.Control.Click>事件處理常式，並填寫事件處理常式，如以下代碼示例所示。</span><span class="sxs-lookup"><span data-stu-id="435eb-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
    ```csharp  
    private void previousButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position - 1;  
    }  
  
    private void nextButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position + 1;  
    }  
    ```  
  
    ```vb  
    Private Sub PreviousButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles PreviousButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position - 1  
    End Sub  
  
    Private Sub NextButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles NextButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position + 1  
    End Sub  
    ```  
  
9. <span data-ttu-id="435eb-119">執行範例。</span><span class="sxs-lookup"><span data-stu-id="435eb-119">Run the sample.</span></span> <span data-ttu-id="435eb-120">編輯資料，並使用 **"上一步**"和 **"下一步**"按鈕查看資料已正確保存到 。 <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="435eb-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="435eb-121">範例</span><span class="sxs-lookup"><span data-stu-id="435eb-121">Example</span></span>  
 <span data-ttu-id="435eb-122">以下代碼示例是完成上一個過程後產生的完整代碼清單。</span><span class="sxs-lookup"><span data-stu-id="435eb-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="435eb-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="435eb-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="435eb-124">創建視覺化 C# 或視覺化基本專案。</span><span class="sxs-lookup"><span data-stu-id="435eb-124">Create a Visual C# or Visual Basic project.</span></span>  
  
- <span data-ttu-id="435eb-125">將<xref:System.Windows.Forms.TextBox>和<xref:System.Windows.Forms.MaskedTextBox>控制項添加到表單中，如上一過程所述。</span><span class="sxs-lookup"><span data-stu-id="435eb-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
- <span data-ttu-id="435eb-126">打開專案的預設表單的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="435eb-126">Open the source code file for the project's default form.</span></span>  
  
- <span data-ttu-id="435eb-127">將此檔中的原始程式碼替換為上一個"代碼"部分中列出的代碼。</span><span class="sxs-lookup"><span data-stu-id="435eb-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
- <span data-ttu-id="435eb-128">編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="435eb-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435eb-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="435eb-129">See also</span></span>

- [<span data-ttu-id="435eb-130">逐步解說：使用 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="435eb-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
