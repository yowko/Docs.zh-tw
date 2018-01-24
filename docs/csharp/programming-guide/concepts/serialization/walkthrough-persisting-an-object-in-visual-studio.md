---
title: "逐步解說：在 Visual Studio 中保存物件 (#C)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b1a3fc377875ee25baa0718a25b5ac509822154
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a>逐步解說：在 Visual Studio 中保存物件 (#C)
雖然您可以在設計階段將物件的屬性設為預設值，但當物件終結時，於執行階段輸入的任何值都會遺失。 您可以使用序列化來保存執行個體之間的物件資料，藉此儲存值，並在下次將物件具現化時加以擷取。  
  
 在本逐步解說中，您將建立簡單的 `Loan` 物件，並將其資料保存至檔案。 當您重新建立物件時，即會從檔案擷取資料。  
  
> [!IMPORTANT]
>  如果檔案不存在，此範例就會建立新的檔案。 如果應用程式需要建立檔案，該應用程式就必須具有 `Create` 資料夾的權限。 您可以使用存取控制清單來設定權限。 如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。 若有可能，更為安全的做法是在部署期間建立檔案，並只授與單一檔案的 `Read` 權限 (而不是資料夾的 Create 權限)。 此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。  
  
> [!IMPORTANT]
>  這個範例會使用二進位格式檔案來儲存資料。 這些格式不適用於敏感性資料，例如密碼或信用卡資訊。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="creating-the-loan-object"></a>建立 Loan 物件  
 第一個步驟是建立 `Loan` 類別，以及使用該類別的測試應用程式。  
  
### <a name="to-create-the-loan-class"></a>若要建立 Loan 類別  
  
1.  建立新的類別庫專案，並將它命名為 "LoanClass"。 如需詳細資訊，請參閱[建立方案與專案](/visualstudio/ide/creating-solutions-and-projects)。  
  
2.  在方案總管中，開啟 Class1 檔案的捷徑功能表，然後選擇 [重新命名] 。 將檔案重新命名為 `Loan`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `Loan`。  
  
3.  將下列 Public 成員新增至類別：  
  
    ```csharp  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
        public double LoanAmount {get; set;}  
        public double InterestRate {get; set;}  
        public int Term {get; set;}  
  
        private string p_Customer;  
        public string Customer  
        {  
            get { return p_Customer; }  
            set   
            {  
                p_Customer = value;  
                PropertyChanged(this,  
                  new System.ComponentModel.PropertyChangedEventArgs("Customer"));  
            }  
        }  
  
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
  
        public Loan(double loanAmount,  
                    double interestRate,  
                    int term,  
                    string customer)  
        {  
            this.LoanAmount = loanAmount;  
            this.InterestRate = interestRate;  
            this.Term = term;  
            p_Customer = customer;  
        }  
    }  
    ```  
  
 您還必須建立使用 `Loan` 類別的簡單應用程式。  
  
### <a name="to-create-a-test-application"></a>若要建立測試應用程式  
  
1.  若要將 Windows Forms 應用程式專案新增至方案，請在 [檔案] 功能表上，選擇 [新增專案]。  
  
2.  在 [新增專案] 對話方塊中，選擇 [Windows Forms 應用程式]，並輸入 `LoanApp` 作為專案名稱，然後按一下 [確定] 以關閉對話方塊。  
  
3.  在方案總管中，選擇 LoanApp 專案。  
  
4.  在 [專案] 功能表上，選擇 [設定為啟始專案]。  
  
5.  在 [專案]  功能表上，選擇 [加入參考] 。  
  
6.  在 [新增參考] 對話方塊中，依序選擇 [專案] 索引標籤和 LoanClass 專案。  
  
7.  按一下 [確定]  關閉對話方塊。  
  
8.  在設計工具中，將四個 <xref:System.Windows.Forms.TextBox> 控制項加入表單。  
  
9. 在程式碼編輯器中，加入下列程式碼：  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
10. 使用下列程式碼，將 `PropertyChanged` 事件的事件處理常式新增至表單：  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 您現在可以建置並執行應用程式。 請注意，文字方塊中會顯示來自 `Loan` 類別的預設值。 您可嘗試將 7.5 的利率值變更為 7.1，然後關閉應用程式，再執行一次；該值即會還原成預設值 7.5。  
  
 在現實生活中，利率會定期變更，但不一定每次都需要執行應用程式。 與其讓使用者每次都隨著應用程式執行時間來更新利率，較好的做法是保存應用程式執行個體之間的最新利率。 在下一個步驟中，您會將序列化新增至 Loan 類別以進行上述作業。  
  
## <a name="using-serialization-to-persist-the-object"></a>使用序列化來保存物件  
 為了保存 Loan 類別的值，您必須先使用 `Serializable` 屬性來標示類別。  
  
### <a name="to-mark-a-class-as-serializable"></a>若要將類別標示為可序列化  
  
-   變更 Loan 類別的類別宣告，如下所示：  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 編譯器接收到 `Serializable` 屬性時，即會了解類別中的所有項目皆可保存至檔案。 `PropertyChanged` 事件是由 Windows Form 物件處理，因此無法序列化。 `NonSerialized` 屬性可以用來標示不應保存的類別成員。  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>若要避免將成員序列化  
  
-   變更 `PropertyChanged` 事件的宣告，如下所示：  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 下一個步驟是將序列化程式碼新增至 LoanApp 應用程式。 若要序列化類別並將它寫入檔案，您必須使用 <xref:System.IO> 和 <xref:System.Xml.Serialization> 命名空間。 若要避免輸入完整的名稱，您可以新增必要類別庫的參考。  
  
### <a name="to-add-references-to-namespaces"></a>若要新增命名空間的參考  
  
-   在 `Form1` 類別最上方新增下列陳述式：  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     在此情況下，您會使用二進位格式器，將物件儲存為二進位格式。  
  
 下一個步驟是新增程式碼，以在建立物件時，從檔案還原序列化物件。  
  
### <a name="to-deserialize-an-object"></a>還原序列化物件  
  
1.  將常數新增至已序列化資料檔案名稱的類別。  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  修改 `Form1_Load` 事件程序中的程式碼，如下所示：  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        if (File.Exists(FileName))  
        {  
            Stream TestFileStream = File.OpenRead(FileName);  
            BinaryFormatter deserializer = new BinaryFormatter();  
            TestLoan = (LoanClass.Loan)deserializer.Deserialize(TestFileStream);  
            TestFileStream.Close();  
        }  
  
        TestLoan.PropertyChanged += this.CustomerPropertyChanged;  
  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
     請注意，您必須先檢查檔案是否存在。 如果存在的話，請建立 <xref:System.IO.Stream> 類別以讀取二進位檔案，並建立 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 類別來轉譯該檔案。 您也需要將資料流類型轉換成 Loan 物件類型。  
  
 然後，您必須新增程式碼，以將文字方塊中輸入的資料儲存到 `Loan` 類別，接著必須將類別序列化至檔案。  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>若要儲存資料以及序列化類別  
  
-   將下列程式碼新增至 `Form1_FormClosing` 事件程序中：  
  
    ```csharp  
    private void Form1_FormClosing(object sender, FormClosingEventArgs e)  
    {  
        TestLoan.LoanAmount = Convert.ToDouble(textBox1.Text);  
        TestLoan.InterestRate = Convert.ToDouble(textBox2.Text);  
        TestLoan.Term = Convert.ToInt32(textBox3.Text);  
        TestLoan.Customer = textBox4.Text;  
  
        Stream TestFileStream = File.Create(FileName);  
        BinaryFormatter serializer = new BinaryFormatter();  
        serializer.Serialize(TestFileStream, TestLoan);  
        TestFileStream.Close();  
    }  
    ```  
  
 您現在可以再次建置並執行應用程式。 一開始，文字方塊中會顯示預設值。 請嘗試變更值，並在第四個文字方塊中輸入名稱。 關閉應用程式，然後再重新執行。 請注意，現在文字方塊中會出現新的值。  
  
## <a name="see-also"></a>請參閱  
 [序列化 (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [C# 程式設計指南](../../../../csharp/programming-guide/index.md)
