---
title: "逐步解說：在 Visual Studio 中保存物件 (#C)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4c8dce64c470f01f540a83f68e3861df56913e4c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a><span data-ttu-id="b1cfe-102">逐步解說：在 Visual Studio 中保存物件 (#C)</span><span class="sxs-lookup"><span data-stu-id="b1cfe-102">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>
<span data-ttu-id="b1cfe-103">雖然您可以在設計階段將物件的屬性設為預設值，但當物件終結時，於執行階段輸入的任何值都會遺失。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="b1cfe-104">您可以使用序列化來保存執行個體之間的物件資料，藉此儲存值，並在下次將物件具現化時加以擷取。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
 <span data-ttu-id="b1cfe-105">在本逐步解說中，您將建立簡單的 `Loan` 物件，並將其資料保存至檔案。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-105">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="b1cfe-106">當您重新建立物件時，即會從檔案擷取資料。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-106">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1cfe-107">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="b1cfe-108">如果應用程式需要建立檔案，該應用程式就必須具有 `Create` 資料夾的權限。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-108">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="b1cfe-109">您可以使用存取控制清單來設定權限。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="b1cfe-110">如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="b1cfe-111">若有可能，更為安全的做法是在部署期間建立檔案，並只授與單一檔案的 `Read` 權限 (而不是資料夾的 Create 權限)。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-111">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="b1cfe-112">此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-112">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1cfe-113">這個範例會使用二進位格式檔案來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="b1cfe-114">這些格式不適用於敏感性資料，例如密碼或信用卡資訊。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1cfe-115">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b1cfe-116">若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-116">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b1cfe-117">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="b1cfe-118">建立 Loan 物件</span><span class="sxs-lookup"><span data-stu-id="b1cfe-118">Creating the Loan Object</span></span>  
 <span data-ttu-id="b1cfe-119">第一個步驟是建立 `Loan` 類別，以及使用該類別的測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-119">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="b1cfe-120">若要建立 Loan 類別</span><span class="sxs-lookup"><span data-stu-id="b1cfe-120">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="b1cfe-121">建立新的類別庫專案，並將它命名為 "LoanClass"。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-121">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="b1cfe-122">如需詳細資訊，請參閱[建立方案與專案](/visualstudio/ide/creating-solutions-and-projects)。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-122">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="b1cfe-123">在方案總管中，開啟 Class1 檔案的捷徑功能表，然後選擇 [重新命名] 。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-123">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="b1cfe-124">將檔案重新命名為 `Loan`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-124">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="b1cfe-125">重新命名檔案時，也會將類別重新命名為 `Loan`。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-125">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="b1cfe-126">將下列 Public 成員新增至類別：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-126">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="b1cfe-127">您還必須建立使用 `Loan` 類別的簡單應用程式。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-127">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="b1cfe-128">若要建立測試應用程式</span><span class="sxs-lookup"><span data-stu-id="b1cfe-128">To create a test application</span></span>  
  
1.  <span data-ttu-id="b1cfe-129">若要將 Windows Forms 應用程式專案新增至方案，請在 [檔案] 功能表上，選擇 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-129">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="b1cfe-130">在 [新增專案] 對話方塊中，選擇 [Windows Forms 應用程式]，並輸入 `LoanApp` 作為專案名稱，然後按一下 [確定] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-130">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="b1cfe-131">在方案總管中，選擇 LoanApp 專案。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-131">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="b1cfe-132">在 [專案] 功能表上，選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-132">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="b1cfe-133">在 [專案]  功能表上，選擇 [加入參考] 。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-133">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="b1cfe-134">在 [新增參考] 對話方塊中，依序選擇 [專案] 索引標籤和 LoanClass 專案。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-134">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="b1cfe-135">按一下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-135">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="b1cfe-136">在設計工具中，將四個 <xref:System.Windows.Forms.TextBox> 控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-136">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="b1cfe-137">在程式碼編輯器中，加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-137">In the Code Editor, add the following code:</span></span>  
  
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
  
10. <span data-ttu-id="b1cfe-138">使用下列程式碼，將 `PropertyChanged` 事件的事件處理常式新增至表單：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-138">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 <span data-ttu-id="b1cfe-139">您現在可以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-139">At this point, you can build and run the application.</span></span> <span data-ttu-id="b1cfe-140">請注意，文字方塊中會顯示來自 `Loan` 類別的預設值。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-140">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="b1cfe-141">您可嘗試將 7.5 的利率值變更為 7.1，然後關閉應用程式，再執行一次；該值即會還原成預設值 7.5。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-141">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="b1cfe-142">在現實生活中，利率會定期變更，但不一定每次都需要執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-142">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="b1cfe-143">與其讓使用者每次都隨著應用程式執行時間來更新利率，較好的做法是保存應用程式執行個體之間的最新利率。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-143">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="b1cfe-144">在下一個步驟中，您會將序列化新增至 Loan 類別以進行上述作業。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-144">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="b1cfe-145">使用序列化來保存物件</span><span class="sxs-lookup"><span data-stu-id="b1cfe-145">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="b1cfe-146">為了保存 Loan 類別的值，您必須先使用 `Serializable` 屬性來標示類別。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-146">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="b1cfe-147">若要將類別標示為可序列化</span><span class="sxs-lookup"><span data-stu-id="b1cfe-147">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="b1cfe-148">變更 Loan 類別的類別宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-148">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 <span data-ttu-id="b1cfe-149">編譯器接收到 `Serializable` 屬性時，即會了解類別中的所有項目皆可保存至檔案。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-149">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="b1cfe-150">`PropertyChanged` 事件是由 Windows Form 物件處理，因此無法序列化。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-150">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="b1cfe-151">`NonSerialized` 屬性可以用來標示不應保存的類別成員。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-151">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="b1cfe-152">若要避免將成員序列化</span><span class="sxs-lookup"><span data-stu-id="b1cfe-152">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="b1cfe-153">變更 `PropertyChanged` 事件的宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-153">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 <span data-ttu-id="b1cfe-154">下一個步驟是將序列化程式碼新增至 LoanApp 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-154">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="b1cfe-155">若要序列化類別並將它寫入檔案，您必須使用 <xref:System.IO> 和 <xref:System.Xml.Serialization> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-155">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="b1cfe-156">若要避免輸入完整的名稱，您可以新增必要類別庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-156">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="b1cfe-157">若要新增命名空間的參考</span><span class="sxs-lookup"><span data-stu-id="b1cfe-157">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="b1cfe-158">在 `Form1` 類別最上方新增下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-158">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     <span data-ttu-id="b1cfe-159">在此情況下，您會使用二進位格式器，將物件儲存為二進位格式。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-159">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="b1cfe-160">下一個步驟是新增程式碼，以在建立物件時，從檔案還原序列化物件。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-160">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="b1cfe-161">還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="b1cfe-161">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="b1cfe-162">將常數新增至已序列化資料檔案名稱的類別。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-162">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  <span data-ttu-id="b1cfe-163">修改 `Form1_Load` 事件程序中的程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-163">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="b1cfe-164">請注意，您必須先檢查檔案是否存在。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-164">Note that you first must check that the file exists.</span></span> <span data-ttu-id="b1cfe-165">如果存在的話，請建立 <xref:System.IO.Stream> 類別以讀取二進位檔案，並建立 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 類別來轉譯該檔案。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-165">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="b1cfe-166">您也需要將資料流類型轉換成 Loan 物件類型。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-166">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="b1cfe-167">然後，您必須新增程式碼，以將文字方塊中輸入的資料儲存到 `Loan` 類別，接著必須將類別序列化至檔案。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-167">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="b1cfe-168">若要儲存資料以及序列化類別</span><span class="sxs-lookup"><span data-stu-id="b1cfe-168">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="b1cfe-169">將下列程式碼新增至 `Form1_FormClosing` 事件程序中：</span><span class="sxs-lookup"><span data-stu-id="b1cfe-169">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="b1cfe-170">您現在可以再次建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-170">At this point, you can again build and run the application.</span></span> <span data-ttu-id="b1cfe-171">一開始，文字方塊中會顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-171">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="b1cfe-172">請嘗試變更值，並在第四個文字方塊中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-172">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="b1cfe-173">關閉應用程式，然後再重新執行。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-173">Close the application and then run it again.</span></span> <span data-ttu-id="b1cfe-174">請注意，現在文字方塊中會出現新的值。</span><span class="sxs-lookup"><span data-stu-id="b1cfe-174">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cfe-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1cfe-175">See Also</span></span>  
 <span data-ttu-id="b1cfe-176">[序列化 (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1cfe-176">[Serialization (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md) </span></span>  
 [<span data-ttu-id="b1cfe-177">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b1cfe-177">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)

