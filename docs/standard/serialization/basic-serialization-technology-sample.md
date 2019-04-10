---
title: 基本序列化技術範例
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: dc190a93e45bf2b682aff0158ccd42bc09762d9a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315006"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="9d035-102">基本序列化技術範例</span><span class="sxs-lookup"><span data-stu-id="9d035-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="9d035-103">下載範例</span><span class="sxs-lookup"><span data-stu-id="9d035-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="9d035-104">這個範例會說明 Common Language Runtime 將記憶體中的物件 Graph 序列化為資料流的能力。</span><span class="sxs-lookup"><span data-stu-id="9d035-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="9d035-105">這個範例可以使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 進行序列化。</span><span class="sxs-lookup"><span data-stu-id="9d035-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="9d035-106">一個內含資料的連結串列 (Linked List)，會序列化為檔案資料流或從檔案資料流還原序列化。</span><span class="sxs-lookup"><span data-stu-id="9d035-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="9d035-107">在這兩種情形下，清單都會顯示供您查看結果。</span><span class="sxs-lookup"><span data-stu-id="9d035-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="9d035-108">連結串列的型別為 `LinkedList`，是這個範例所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="9d035-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="9d035-109">如需序列化的詳細資訊，請檢視原始程式碼和 build.proj 檔案中的註解。</span><span class="sxs-lookup"><span data-stu-id="9d035-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="9d035-110">若要使用命令提示字元建置範例</span><span class="sxs-lookup"><span data-stu-id="9d035-110">To build the sample using the Command Prompt</span></span>  
  
1. <span data-ttu-id="9d035-111">使用 [命令提示字元]，巡覽至 Technologies\Serialization\Runtime Serialization\Basic 目錄下的其中一個語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="9d035-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2. <span data-ttu-id="9d035-112">根據您選擇的程式設計語言，在命令列鍵入 **msbuild SerializationCS.sln**、**msbuild SerializationJSL.sln** 或 **msbuild SerializationVB.sln**。</span><span class="sxs-lookup"><span data-stu-id="9d035-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="9d035-113">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="9d035-113">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="9d035-114">開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，並巡覽至此範例任一程式設計語言的子目錄。</span><span class="sxs-lookup"><span data-stu-id="9d035-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="9d035-115">根據您選擇的程式設計語言，按兩下 SerializationCS.sln、SerializationJSL.sln 或 SerializationVB.sln 檔案的圖示，在 Visual Studio 中開啟這個檔案。</span><span class="sxs-lookup"><span data-stu-id="9d035-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3. <span data-ttu-id="9d035-116">在 [建置] 功能表中，選取 [建置方案]。</span><span class="sxs-lookup"><span data-stu-id="9d035-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="9d035-117">這個範例應用程式將建置於預設的 \bin 或 \bin\Debug 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="9d035-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="9d035-118">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="9d035-118">To run the sample</span></span>  
  
1. <span data-ttu-id="9d035-119">巡覽至包含已建置之可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="9d035-119">Navigate to the directory containing the built executable.</span></span>  
  
2. <span data-ttu-id="9d035-120">在命令列鍵入 **Serialization.exe** 以及您想要的參數值。</span><span class="sxs-lookup"><span data-stu-id="9d035-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9d035-121">這個範例會建置一個主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d035-121">This sample builds a console application.</span></span> <span data-ttu-id="9d035-122">您必須使用命令提示字元啟動，才能檢視它的輸出。</span><span class="sxs-lookup"><span data-stu-id="9d035-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d035-123">備註</span><span class="sxs-lookup"><span data-stu-id="9d035-123">Remarks</span></span>  
 <span data-ttu-id="9d035-124">這個範例應用程式接受會指出您想執行哪一項測試的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="9d035-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="9d035-125">若想使用 SOAP 格式子，將包含 10 個節點的清單序列化成名為 **Test.xml** 的檔案，請使用 **sx Test.xml 10** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d035-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="9d035-126">例如：</span><span class="sxs-lookup"><span data-stu-id="9d035-126">For Example:</span></span>  
  
 **<span data-ttu-id="9d035-127">Serialize.exe -sx Test.xml 10</span><span class="sxs-lookup"><span data-stu-id="9d035-127">Serialize.exe -sx Test.xml 10</span></span>**  
  
 <span data-ttu-id="9d035-128">如果想還原序列化前一個範例的 **Test.xml** 檔案，請使用 **dx Test.xml** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d035-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="9d035-129">例如：</span><span class="sxs-lookup"><span data-stu-id="9d035-129">For Example:</span></span>  
  
 **<span data-ttu-id="9d035-130">Serialize.exe -dx Test.xml</span><span class="sxs-lookup"><span data-stu-id="9d035-130">Serialize.exe -dx Test.xml</span></span>**  
  
 <span data-ttu-id="9d035-131">在上述兩個範例中，命令列參數中的 "x" 表示您想執行 XML SOAP 序列化。</span><span class="sxs-lookup"><span data-stu-id="9d035-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="9d035-132">如果在相同的位置上使用 "b"，就表示要使用二進位序列化。</span><span class="sxs-lookup"><span data-stu-id="9d035-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="9d035-133">如果您想嘗試序列化大量的節點，可以將主控台輸出重新導向至檔案中。</span><span class="sxs-lookup"><span data-stu-id="9d035-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="9d035-134">例如：</span><span class="sxs-lookup"><span data-stu-id="9d035-134">For Example:</span></span>  
  
 **<span data-ttu-id="9d035-135">Serialize.exe -sb Test.bin 10000 >somefile.txt</span><span class="sxs-lookup"><span data-stu-id="9d035-135">Serialize.exe -sb Test.bin 10000 >somefile.txt</span></span>**  
  
 <span data-ttu-id="9d035-136">下面幾點簡短說明了此範例所使用的類別和技術。</span><span class="sxs-lookup"><span data-stu-id="9d035-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
-   <span data-ttu-id="9d035-137">執行階段序列化</span><span class="sxs-lookup"><span data-stu-id="9d035-137">Runtime Serialization</span></span>  
  
    -   <xref:System.Runtime.Serialization.IFormatter> <span data-ttu-id="9d035-138">用來參考<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>或<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>物件。</span><span class="sxs-lookup"><span data-stu-id="9d035-138">Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <span data-ttu-id="9d035-139">用來序列化中一種二進位格式的資料流的連結的清單。</span><span class="sxs-lookup"><span data-stu-id="9d035-139">Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="9d035-140">二進位格式子使用的格式只有 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 型別才了解。</span><span class="sxs-lookup"><span data-stu-id="9d035-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="9d035-141">不過，資料相當簡明。</span><span class="sxs-lookup"><span data-stu-id="9d035-141">However, the data is concise.</span></span>  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> <span data-ttu-id="9d035-142">用來序列化至 SOAP 格式的資料流的連結的清單。</span><span class="sxs-lookup"><span data-stu-id="9d035-142">Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="9d035-143">SOAP 是一種標準格式。</span><span class="sxs-lookup"><span data-stu-id="9d035-143">SOAP is a standard format.</span></span>  
  
-   <span data-ttu-id="9d035-144">資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="9d035-144">Stream I/O</span></span>  
  
    -   <xref:System.IO.Stream> <span data-ttu-id="9d035-145">用來序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="9d035-145">Used to serialize and deserialize.</span></span> <span data-ttu-id="9d035-146">這個範例所用的特定資料流型別是 <xref:System.IO.FileStream> 型別。</span><span class="sxs-lookup"><span data-stu-id="9d035-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="9d035-147">不過，序列化可以使用衍生自 <xref:System.IO.Stream> 的任何型別。</span><span class="sxs-lookup"><span data-stu-id="9d035-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    -   <xref:System.IO.File> <span data-ttu-id="9d035-148">用來建立<xref:System.IO.FileStream>物件來讀取及建立磁碟上的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d035-148">Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    -   <xref:System.IO.FileStream> <span data-ttu-id="9d035-149">用來序列化和還原序列化連結的清單。</span><span class="sxs-lookup"><span data-stu-id="9d035-149">Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d035-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d035-150">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="9d035-151">基本序列化</span><span class="sxs-lookup"><span data-stu-id="9d035-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="9d035-152">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="9d035-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="9d035-153">使用屬性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="9d035-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="9d035-154">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="9d035-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="9d035-155">序列化</span><span class="sxs-lookup"><span data-stu-id="9d035-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="9d035-156">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="9d035-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
