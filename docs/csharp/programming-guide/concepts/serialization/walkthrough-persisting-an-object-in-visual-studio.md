---
title: 逐步解說：使用 C# 保存物件
ms.date: 04/26/2018
ms.openlocfilehash: 88fb589ca2f9a24f861b528bfd601f837e9aac5f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105928"
---
# <a name="walkthrough-persisting-an-object-using-c"></a><span data-ttu-id="50149-102">逐步解說：使用 C\# 保存物件</span><span class="sxs-lookup"><span data-stu-id="50149-102">Walkthrough: persisting an object using C\#</span></span>

<span data-ttu-id="50149-103">您可以使用序列化來保存執行個體之間的物件資料，藉此儲存值，並在下次將物件具現化時加以擷取。</span><span class="sxs-lookup"><span data-stu-id="50149-103">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>

<span data-ttu-id="50149-104">在本逐步解說中，您將建立基本的 `Loan` 物件，並將其資料保存至檔案。</span><span class="sxs-lookup"><span data-stu-id="50149-104">In this walkthrough, you will create a basic `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="50149-105">當您重新建立物件時，即會從檔案擷取資料。</span><span class="sxs-lookup"><span data-stu-id="50149-105">You will then retrieve the data from the file when you re-create the object.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50149-106">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="50149-106">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="50149-107">如果應用程式需要建立檔案，該應用程式就必須具有資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="50149-107">If an application must create a file, that application must have `Create` permission for the folder.</span></span> <span data-ttu-id="50149-108">您可以使用存取控制清單來設定權限。</span><span class="sxs-lookup"><span data-stu-id="50149-108">Permissions are set by using access control lists.</span></span> <span data-ttu-id="50149-109">如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="50149-109">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="50149-110">若有可能，更為安全的做法是在部署期間建立檔案，並只授與單一檔案的 `Read` 權限 (而不是資料夾的 Create 權限)。</span><span class="sxs-lookup"><span data-stu-id="50149-110">Where possible, it's more secure to create the file during deployment and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="50149-111">此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。</span><span class="sxs-lookup"><span data-stu-id="50149-111">Also, it's more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50149-112">這個範例會使用二進位格式檔案來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="50149-112">This example stores data in a binary format file.</span></span> <span data-ttu-id="50149-113">這些格式不適用於敏感性資料，例如密碼或信用卡資訊。</span><span class="sxs-lookup"><span data-stu-id="50149-113">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="50149-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="50149-114">Prerequisites</span></span>

- <span data-ttu-id="50149-115">若要建置並執行，請安裝 [.NET Core SDK](https://www.microsoft.com/net/core)。</span><span class="sxs-lookup"><span data-stu-id="50149-115">To build and run, install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span>

- <span data-ttu-id="50149-116">如果您還沒有這麼做，請安裝您慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="50149-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="50149-117">需要安裝程式碼編輯器嗎？</span><span class="sxs-lookup"><span data-stu-id="50149-117">Need to install a code editor?</span></span> <span data-ttu-id="50149-118">試用 [Visual Studio](https://visualstudio.com/downloads)！</span><span class="sxs-lookup"><span data-stu-id="50149-118">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

- <span data-ttu-id="50149-119">範例需要 C# 7.3。</span><span class="sxs-lookup"><span data-stu-id="50149-119">The example requires C# 7.3.</span></span> <span data-ttu-id="50149-120">請參閱[選取 C# 語言版本](../../../language-reference/configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="50149-120">See [Select the C# language version](../../../language-reference/configure-language-version.md)</span></span> 

<span data-ttu-id="50149-121">您可以在 [.NET 範例 GitHub 存放庫](https://github.com/dotnet/samples/tree/master/csharp/serialization) (英文) 線上檢查範例程式程。</span><span class="sxs-lookup"><span data-stu-id="50149-121">You can examine the sample code online [at the .NET samples GitHub repository](https://github.com/dotnet/samples/tree/master/csharp/serialization).</span></span>

## <a name="creating-the-loan-object"></a><span data-ttu-id="50149-122">建立 Loan 物件</span><span class="sxs-lookup"><span data-stu-id="50149-122">Creating the loan object</span></span>

<span data-ttu-id="50149-123">第一個步驟是建立 `Loan` 類別，以及使用該類別的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="50149-123">The first step is to create a `Loan` class and a console application that uses the class:</span></span>

1. <span data-ttu-id="50149-124">建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="50149-124">Create a new application.</span></span> <span data-ttu-id="50149-125">輸入 `dotnet new console -o serialization`，在名為 `serialization` 的子目錄中建立新的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="50149-125">Type `dotnet new console -o serialization` to create a new console application in a subdirectory named `serialization`.</span></span>
1. <span data-ttu-id="50149-126">在編輯器中開啟應用程式，並新增名為 `Loan.cs` 的新類別。</span><span class="sxs-lookup"><span data-stu-id="50149-126">Open the application in your editor, and add a new class named `Loan.cs`.</span></span>
1. <span data-ttu-id="50149-127">將下列程式碼新增至 `Loan` 類別：</span><span class="sxs-lookup"><span data-stu-id="50149-127">Add the following code to your `Loan` class:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

<span data-ttu-id="50149-128">您還必須建立使用 `Loan` 類別的應用程式。</span><span class="sxs-lookup"><span data-stu-id="50149-128">You will also have to create an application that uses the `Loan` class.</span></span>

## <a name="serialize-the-loan-object"></a><span data-ttu-id="50149-129">序列化 Loan 物件</span><span class="sxs-lookup"><span data-stu-id="50149-129">Serialize the loan object</span></span>

1. <span data-ttu-id="50149-130">開啟 `Program.cs`。</span><span class="sxs-lookup"><span data-stu-id="50149-130">Open `Program.cs`.</span></span> <span data-ttu-id="50149-131">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="50149-131">Add the following code:</span></span>

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

<span data-ttu-id="50149-132">為 `PropertyChanged` 事件新增事件處理常式，並新增幾行來修改 `Loan` 物件和顯示所做的變更。</span><span class="sxs-lookup"><span data-stu-id="50149-132">Add an event handler for the `PropertyChanged` event, and a few lines to modify the `Loan` object and display the changes.</span></span> <span data-ttu-id="50149-133">您可以在下列程式碼中看到新增的項目：</span><span class="sxs-lookup"><span data-stu-id="50149-133">You can see the additions in the following code:</span></span>

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

<span data-ttu-id="50149-134">此時，您可以執行該程式碼，並查看目前的輸出：</span><span class="sxs-lookup"><span data-stu-id="50149-134">At this point, you can run the code, and see the current output:</span></span>

```console
New customer value: Henry Clay
7.5
7.1
```

<span data-ttu-id="50149-135">執行此應用程式一律會重複寫入相同的值。</span><span class="sxs-lookup"><span data-stu-id="50149-135">Running this application repeatedly always writes the same values.</span></span> <span data-ttu-id="50149-136">每次您執行程式時，就會建立一個新的 Loan 物件。</span><span class="sxs-lookup"><span data-stu-id="50149-136">A new Loan object is created every time you run the program.</span></span> <span data-ttu-id="50149-137">在現實生活中，利率會定期變更，但不一定每次都需要執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="50149-137">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="50149-138">序列化程式碼表示您要保存應用程式執行個體之間的最近利率。</span><span class="sxs-lookup"><span data-stu-id="50149-138">Serialization code means you preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="50149-139">在下一個步驟中，您會將序列化新增至 Loan 類別以進行上述作業。</span><span class="sxs-lookup"><span data-stu-id="50149-139">In the next step, you will do just that by adding serialization to the Loan class.</span></span>

## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="50149-140">使用序列化來保存物件</span><span class="sxs-lookup"><span data-stu-id="50149-140">Using Serialization to Persist the Object</span></span>

<span data-ttu-id="50149-141">為了保存 Loan 類別的值，您必須先使用 `Serializable` 屬性來標示類別。</span><span class="sxs-lookup"><span data-stu-id="50149-141">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span> <span data-ttu-id="50149-142">在 Loan 類別定義之上新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="50149-142">Add the following code above the Loan class definition:</span></span>

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

<span data-ttu-id="50149-143">編譯器接收到 <xref:System.SerializableAttribute> 時，即會了解類別中的所有項目皆可保存至檔案。</span><span class="sxs-lookup"><span data-stu-id="50149-143">The <xref:System.SerializableAttribute> tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="50149-144">因為 `PropertyChanged` 事件不代表應儲存之物件圖形的一部分，所以它不應該被序列化。</span><span class="sxs-lookup"><span data-stu-id="50149-144">Because the `PropertyChanged` event does not represent part of the object graph that should be stored, it should not be serialized.</span></span> <span data-ttu-id="50149-145">這樣做會序列化附加至該事件的所有物件。</span><span class="sxs-lookup"><span data-stu-id="50149-145">Doing so would serialize all objects that are attached to that event.</span></span> <span data-ttu-id="50149-146">您可以將 <xref:System.NonSerializedAttribute> 新增至 `PropertyChanged` 事件處理常式的欄位宣告。</span><span class="sxs-lookup"><span data-stu-id="50149-146">You can add the <xref:System.NonSerializedAttribute> to the field declaration for the `PropertyChanged` event handler.</span></span>

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

<span data-ttu-id="50149-147">從 C# 7.3 開始，您可以使用 `field` 目標值，將屬性 (attribute) 附加至使用自動實作屬性 (property) 的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="50149-147">Beginning with C# 7.3, you can attach attributes to the backing field of an auto-implemented property using the `field` target value.</span></span> <span data-ttu-id="50149-148">下列程式碼會新增 `TimeLastLoaded` 屬性，並將它標示為不可序列化：</span><span class="sxs-lookup"><span data-stu-id="50149-148">The following code adds a `TimeLastLoaded` property and marks it as not serializable:</span></span>

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

<span data-ttu-id="50149-149">下一個步驟是將序列化程式碼新增至 LoanApp 應用程式。</span><span class="sxs-lookup"><span data-stu-id="50149-149">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="50149-150">若要序列化類別並將它寫入檔案，您必須使用 <xref:System.IO> 和 <xref:System.Runtime.Serialization.Formatters.Binary> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="50149-150">In order to serialize the class and write it to a file, you use the <xref:System.IO> and <xref:System.Runtime.Serialization.Formatters.Binary> namespaces.</span></span> <span data-ttu-id="50149-151">若要避免輸入完整的名稱，您可以新增必要命名空間的參考，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="50149-151">To avoid typing the fully qualified names, you can add references to the necessary namespaces as shown in the following code:</span></span>

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

<span data-ttu-id="50149-152">下一個步驟是新增程式碼，以在建立物件時，從檔案還原序列化物件。</span><span class="sxs-lookup"><span data-stu-id="50149-152">The next step is to add code to deserialize the object from the file when the object is created.</span></span> <span data-ttu-id="50149-153">將常數新增至已序列化資料檔案名稱的類別，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="50149-153">Add a constant to the class for the serialized data's file name as shown in the following code:</span></span>

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

<span data-ttu-id="50149-154">接下來，在建立 `TestLoan` 物件這一行之後新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="50149-154">Next, add the following code after the line that creates the `TestLoan` object:</span></span>

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

<span data-ttu-id="50149-155">您必須先檢查檔案是否存在。</span><span class="sxs-lookup"><span data-stu-id="50149-155">You first must check that the file exists.</span></span> <span data-ttu-id="50149-156">如果存在的話，請建立 <xref:System.IO.Stream> 類別以讀取二進位檔案，並建立 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 類別來轉譯該檔案。</span><span class="sxs-lookup"><span data-stu-id="50149-156">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="50149-157">您也需要將資料流類型轉換成 Loan 物件類型。</span><span class="sxs-lookup"><span data-stu-id="50149-157">You also need to convert from the stream type to the Loan object type.</span></span>

<span data-ttu-id="50149-158">接下來，您必須新增程式碼，將類別序列化為檔案。</span><span class="sxs-lookup"><span data-stu-id="50149-158">Next you must add code to serialize the class to a file.</span></span> <span data-ttu-id="50149-159">在 `Main` 方法的現有程式碼之後，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="50149-159">Add the following code after the existing code in the `Main` method:</span></span>

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

<span data-ttu-id="50149-160">您現在可以再次建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="50149-160">At this point, you can again build and run the application.</span></span> <span data-ttu-id="50149-161">第一次執行時，請注意利率會從 7.5 開始，然後變更為 7.1。</span><span class="sxs-lookup"><span data-stu-id="50149-161">The first time it runs, notice that the interest rates starts at 7.5, and then changes to 7.1.</span></span> <span data-ttu-id="50149-162">關閉應用程式，然後再重新執行。</span><span class="sxs-lookup"><span data-stu-id="50149-162">Close the application and then run it again.</span></span> <span data-ttu-id="50149-163">現在，應用程式會列印訊息，表示它已讀取儲存的檔案，而利率即使在變更它的程式碼之前也是 7.1。</span><span class="sxs-lookup"><span data-stu-id="50149-163">Now, the application prints the message that it has read the saved file, and the interest rate is 7.1 even before the code that changes it.</span></span>

## <a name="see-also"></a><span data-ttu-id="50149-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50149-164">See also</span></span>

- [<span data-ttu-id="50149-165">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="50149-165">Serialization (C#)</span></span>](index.md)
- [<span data-ttu-id="50149-166">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="50149-166">C# Programming Guide</span></span>](../..//index.md)
