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
ms.openlocfilehash: 98d59e7443b51c17baafd05e6701c1418298b4a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530911"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="980b1-102">如何：將資料繫結至 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="980b1-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="980b1-103">您可以將資料繫結<xref:System.Windows.Forms.MaskedTextBox>控制一樣，您可以為任何其他 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="980b1-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="980b1-104">不過，如果資料庫中資料的格式不符合遮罩定義所預期的格式，您必須將資料重新格式化。</span><span class="sxs-lookup"><span data-stu-id="980b1-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="980b1-105">下列程序示範如何使用執行此動作<xref:System.Windows.Forms.Binding.Format>和<xref:System.Windows.Forms.Binding.Parse>事件<xref:System.Windows.Forms.Binding>類別來顯示個別的電話號碼和電話做為單一的可編輯欄位的擴充功能的資料庫欄位。</span><span class="sxs-lookup"><span data-stu-id="980b1-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="980b1-106">下列程序，就需要使用 Northwind 範例資料庫，安裝 SQL Server 資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="980b1-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="980b1-107">將資料繫結至 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="980b1-107">To bind data to a MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="980b1-108">建立新的 Windows Form 專案。</span><span class="sxs-lookup"><span data-stu-id="980b1-108">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="980b1-109">拖放兩<xref:System.Windows.Forms.TextBox>控制項拖曳至表單中; 它們的名稱`FirstName`和`LastName`。</span><span class="sxs-lookup"><span data-stu-id="980b1-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3.  <span data-ttu-id="980b1-110">拖曳<xref:System.Windows.Forms.MaskedTextBox>控制項拖曳至表單，則其命名`PhoneMask`。</span><span class="sxs-lookup"><span data-stu-id="980b1-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4.  <span data-ttu-id="980b1-111">設定<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性`PhoneMask`至`(000) 000-0000 x9999`。</span><span class="sxs-lookup"><span data-stu-id="980b1-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5.  <span data-ttu-id="980b1-112">加入下列命名空間匯入至表單。</span><span class="sxs-lookup"><span data-stu-id="980b1-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6.  <span data-ttu-id="980b1-113">以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="980b1-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="980b1-114">在您的表單類別中的任意位置放置這段程式碼。</span><span class="sxs-lookup"><span data-stu-id="980b1-114">Place this code anywhere in your form class.</span></span>  
  
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
  
7.  <span data-ttu-id="980b1-115">加入事件處理常式<xref:System.Windows.Forms.Binding.Format>和<xref:System.Windows.Forms.Binding.Parse>，結合，並將事件`PhoneNumber`和`Extension`從繫結欄位<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="980b1-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
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
  
8.  <span data-ttu-id="980b1-116">加入兩個<xref:System.Windows.Forms.Button>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="980b1-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="980b1-117">它們的名稱`previousButton`和`nextButton`。</span><span class="sxs-lookup"><span data-stu-id="980b1-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="980b1-118">按兩下每個按鈕，新增<xref:System.Windows.Forms.Control.Click>事件處理常式，並填滿的事件處理常式，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="980b1-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
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
  
9. <span data-ttu-id="980b1-119">執行範例。</span><span class="sxs-lookup"><span data-stu-id="980b1-119">Run the sample.</span></span> <span data-ttu-id="980b1-120">編輯資料，並使用**上一步**和**下一步**按鈕以查看正確的資料保存到<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="980b1-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="980b1-121">範例</span><span class="sxs-lookup"><span data-stu-id="980b1-121">Example</span></span>  
 <span data-ttu-id="980b1-122">下列程式碼範例會列出該結果，無法完成先前的程序的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="980b1-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="980b1-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="980b1-123">Compiling the Code</span></span>  
  
-   <span data-ttu-id="980b1-124">建立 Visual C# 或 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="980b1-124">Create a Visual C# or Visual Basic project.</span></span>  
  
-   <span data-ttu-id="980b1-125">新增<xref:System.Windows.Forms.TextBox>和<xref:System.Windows.Forms.MaskedTextBox>控制項至表單，先前的程序中所述。</span><span class="sxs-lookup"><span data-stu-id="980b1-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
-   <span data-ttu-id="980b1-126">開啟專案的預設表單的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="980b1-126">Open the source code file for the project's default form.</span></span>  
  
-   <span data-ttu-id="980b1-127">上的 < 程式碼 > 一節列出的程式碼取代此檔案中的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="980b1-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
-   <span data-ttu-id="980b1-128">編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="980b1-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980b1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="980b1-129">See Also</span></span>  
 [<span data-ttu-id="980b1-130">逐步解說：使用 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="980b1-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
