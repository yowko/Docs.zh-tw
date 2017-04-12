---
title: "保存物件在 Visual Studio (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0ff6320aee65850b8b445f445f80b4bbe2c9c254
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>逐步解說︰ 保存 Visual Studio (Visual Basic) 中的物件
雖然您可以設定為預設值的物件的屬性在設計階段，在執行階段輸入的任何值都會遺失時終結物件。 您可以使用序列化來保存物件的執行個體，可讓您儲存的值，然後擷取下一次具現化物件之間的資料。  
  
> [!NOTE]
>  在 Visual Basic 中，將簡單的資料，例如名稱或號碼，您可以使用`My.Settings`物件。 如需詳細資訊，請參閱[My.Settings 物件](../../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
 在本逐步解說中，您將建立簡單的`Loan`物件，並將其資料檔案保存。 當您重新建立物件時，會再從檔案擷取資料。  
  
> [!IMPORTANT]
>  如果檔案已經存在，這個範例會建立新的檔案。 如果應用程式必須建立檔案時，該應用程式必須`Create`資料夾的權限。 使用存取控制清單會設定權限。 如果檔案已經存在，應用程式只需要`Write`權限、 較少的權限。 如果可行的話，在部署期間，建立檔案，並僅授與更安全是`Read`（而不是資料夾的建立權限） 的單一檔案的權限。 此外，它是將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾更安全。  
  
> [!IMPORTANT]
>  這個範例會將資料儲存在二進位檔。 這些格式不適用於機密資料，例如密碼或信用卡資訊。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請在 [工具] **** 功能表上按一下 [匯入和匯出設定] **** 。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="creating-the-loan-object"></a>建立貸款物件  
 第一個步驟是建立`Loan`類別和測試應用程式使用的類別。  
  
### <a name="to-create-the-loan-class"></a>若要建立貸款類別  
  
1.  建立新的類別庫專案，並將它 「 LoanClass 」。 如需詳細資訊，請參閱[建立方案與專案](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects)。  
  
2.  在**方案總管] 中**、 開啟 Class1 檔案的捷徑功能表，然後選擇 [**重新命名**。 若要將檔案重新命名`Loan`按下 ENTER。 重新命名檔案也會重新命名類別來`Loan`。  
  
3.  將下列的公用成員加入至類別︰  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 您也會建立簡單的應用程式使用`Loan`類別。  
  
### <a name="to-create-a-test-application"></a>若要建立的測試應用程式  
  
1.  將 Windows Form 應用程式專案加入方案時，加入上**檔案** 功能表上，選擇**新增**，**新的專案**。  
  
2.  中**加入新的專案**對話方塊方塊中，選擇  **Windows Form 應用程式**，並輸入`LoanApp`做為名稱的專案，然後按一下 **確定**以關閉對話方塊。  
  
3.  在**方案總管 中**，選擇 LoanApp 專案。  
  
4.  在**專案**] 功能表上，選擇 [**設定為啟始專案**。  
  
5.  在 [專案] **** 功能表上，選擇 [加入參考] ****。  
  
6.  在**加入參考**對話方塊方塊中，選擇 **專案**索引標籤，然後選擇 LoanClass 專案。  
  
7.  按一下 [確定] **** 關閉對話方塊。  
  
8.  在設計師中，加入四個<xref:System.Windows.Forms.TextBox>控制項加入表單。</xref:System.Windows.Forms.TextBox>  
  
9. 在程式碼編輯器中，加入下列程式碼：  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. 加入事件處理常式`PropertyChanged`事件，以使用下列程式碼形式︰  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 此時，您可以建置並執行應用程式。 請注意，預設值從`Loan`類別會出現在文字方塊中。 嘗試從 7.5 的利率值變更為 7.1，然後關閉應用程式，再執行一次，該值會還原成預設值是 7.5。  
  
 在真實世界中，利率變更定期，但不是一定每次應用程式執行。 與其讓使用者執行應用程式每次更新利率，最好是最新的利率，應用程式的執行個體之間保存。 在下一個步驟中，您將會把剛加入 Loan 類別的序列化。  
  
## <a name="using-serialization-to-persist-the-object"></a>使用序列化來保存物件  
 以便保存貸款類別的值，您必須先將類別標示與`Serializable`屬性。  
  
### <a name="to-mark-a-class-as-serializable"></a>若要將類別標示為可序列化  
  
-   變更 Loan 類別的類別宣告，如下所示︰  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable`屬性會指示編譯器在類別中的所有項目可以保存至檔案。 因為`PropertyChanged`事件由 Windows Form 物件，它不會序列化。 `NonSerialized`屬性可以用來標示不應保存的類別成員。  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>若要避免成員序列化  
  
-   變更的宣告`PropertyChanged`事件，如下所示︰  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 下一個步驟是將序列化程式碼加入至 LoanApp 應用程式。 若要序列化的類別及寫入檔案，您將使用<xref:System.IO>和<xref:System.Xml.Serialization>命名空間。</xref:System.Xml.Serialization> </xref:System.IO> 若要避免輸入完整的名稱，您可以加入必要的類別程式庫的參考。  
  
### <a name="to-add-references-to-namespaces"></a>將參考加入至命名空間  
  
-   將下列陳述式加入至頂端`Form1`類別︰  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     在此情況下，您會使用二進位格式子以二進位格式儲存物件。  
  
 下一個步驟是加入程式碼來建立物件時，還原序列化的物件，從檔案中。  
  
### <a name="to-deserialize-an-object"></a>還原序列化物件  
  
1.  將常數加入至類別，以序列化的資料檔案名稱。  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  修改程式碼中的`Form1_Load`，如下所示的事件程序︰  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     請注意，您首先必須檢查檔案存在。 如果存在的話，建立<xref:System.IO.Stream>類別，以讀取二進位檔案和<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>類別，以將檔案轉譯。</xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> </xref:System.IO.Stream> 您也需要從資料流類型轉換成貸款物件類型。  
  
 接下來，您必須新增到文字方塊中輸入的資料儲存的程式碼`Loan`類別，然後您必須將檔案類別的序列化。  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>若要將資料儲存和序列化類別  
  
-   加入下列程式碼以`Form1_FormClosing`事件程序︰  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 此時，您可以一次建置並執行應用程式。 一開始，預設值會顯示在文字方塊中。 嘗試變更的值，並在第四個文字方塊中輸入的名稱。 關閉應用程式，然後再執行一次。 請注意，新的值現在會出現在文字方塊中。  
  
## <a name="see-also"></a>另請參閱  
 [序列化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)
