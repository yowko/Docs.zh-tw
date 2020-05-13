---
title: 基本序列化技術範例
description: 這個範例會示範如何將記憶體中的物件圖形序列化成資料流程的 CLR 能力。 這個範例可以使用 SoapFormatter 或 BinaryFormatter。
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: fcbf790c3b3d48a0aeb27fd1ef6f75dcd7609ae0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378434"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="70e4f-104">基本序列化技術範例</span><span class="sxs-lookup"><span data-stu-id="70e4f-104">Basic Serialization Technology Sample</span></span>

[<span data-ttu-id="70e4f-105">下載範例</span><span class="sxs-lookup"><span data-stu-id="70e4f-105">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

<span data-ttu-id="70e4f-106">這個範例會說明 Common Language Runtime 將記憶體中的物件 Graph 序列化為資料流的能力。</span><span class="sxs-lookup"><span data-stu-id="70e4f-106">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="70e4f-107">這個範例可以使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 進行序列化。</span><span class="sxs-lookup"><span data-stu-id="70e4f-107">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="70e4f-108">一個內含資料的連結串列 (Linked List)，會序列化為檔案資料流或從檔案資料流還原序列化。</span><span class="sxs-lookup"><span data-stu-id="70e4f-108">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="70e4f-109">在這兩種情形下，清單都會顯示供您查看結果。</span><span class="sxs-lookup"><span data-stu-id="70e4f-109">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="70e4f-110">連結串列的型別為 `LinkedList`，是這個範例所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="70e4f-110">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>

<span data-ttu-id="70e4f-111">如需序列化的詳細資訊，請檢視原始程式碼和 build.proj 檔案中的註解。</span><span class="sxs-lookup"><span data-stu-id="70e4f-111">Review comments in the source code and build.proj files for more information on serialization.</span></span>

### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="70e4f-112">若要使用命令提示字元建置範例</span><span class="sxs-lookup"><span data-stu-id="70e4f-112">To build the sample using the Command Prompt</span></span>

1. <span data-ttu-id="70e4f-113">使用 [命令提示字元]，巡覽至 Technologies\Serialization\Runtime Serialization\Basic 目錄下的其中一個語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="70e4f-113">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>

2. <span data-ttu-id="70e4f-114">根據您選擇的程式設計語言，在命令列鍵入 **msbuild SerializationCS.sln**、**msbuild SerializationJSL.sln** 或 **msbuild SerializationVB.sln**。</span><span class="sxs-lookup"><span data-stu-id="70e4f-114">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>

### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="70e4f-115">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="70e4f-115">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="70e4f-116">開啟 [檔案瀏覽器]，然後流覽至範例的其中一個語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="70e4f-116">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>

2. <span data-ttu-id="70e4f-117">根據您選擇的程式設計語言，按兩下 SerializationCS.sln、SerializationJSL.sln 或 SerializationVB.sln 檔案的圖示，在 Visual Studio 中開啟這個檔案。</span><span class="sxs-lookup"><span data-stu-id="70e4f-117">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="70e4f-118">在 [建置]\*\*\*\* 功能表中，選取 [建置方案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="70e4f-118">In the **Build** menu, select **Build Solution**.</span></span>

 <span data-ttu-id="70e4f-119">這個範例應用程式將建置於預設的 \bin 或 \bin\Debug 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="70e4f-119">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>

### <a name="to-run-the-sample"></a><span data-ttu-id="70e4f-120">執行範例</span><span class="sxs-lookup"><span data-stu-id="70e4f-120">To run the sample</span></span>

1. <span data-ttu-id="70e4f-121">巡覽至包含已建置之可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="70e4f-121">Navigate to the directory containing the built executable.</span></span>

2. <span data-ttu-id="70e4f-122">在命令列鍵入 **Serialization.exe** 以及您想要的參數值。</span><span class="sxs-lookup"><span data-stu-id="70e4f-122">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>

  > [!NOTE]
  > <span data-ttu-id="70e4f-123">這個範例會建置一個主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="70e4f-123">This sample builds a console application.</span></span> <span data-ttu-id="70e4f-124">您必須使用命令提示字元啟動，才能檢視它的輸出。</span><span class="sxs-lookup"><span data-stu-id="70e4f-124">You must launch it using the command prompt in order to view its output.</span></span>

## <a name="remarks"></a><span data-ttu-id="70e4f-125">備註</span><span class="sxs-lookup"><span data-stu-id="70e4f-125">Remarks</span></span>

<span data-ttu-id="70e4f-126">這個範例應用程式接受會指出您想執行哪一項測試的命令列參數。</span><span class="sxs-lookup"><span data-stu-id="70e4f-126">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="70e4f-127">若想使用 SOAP 格式子，將包含 10 個節點的清單序列化成名為 **Test.xml** 的檔案，請使用 **sx Test.xml 10** 參數。</span><span class="sxs-lookup"><span data-stu-id="70e4f-127">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>

<span data-ttu-id="70e4f-128">例如：</span><span class="sxs-lookup"><span data-stu-id="70e4f-128">For Example:</span></span>

```console
Serialize.exe -sx Test.xml 10
```

<span data-ttu-id="70e4f-129">如果想還原序列化前一個範例的 **Test.xml** 檔案，請使用 **dx Test.xml** 參數。</span><span class="sxs-lookup"><span data-stu-id="70e4f-129">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>

<span data-ttu-id="70e4f-130">例如：</span><span class="sxs-lookup"><span data-stu-id="70e4f-130">For Example:</span></span>

```console
Serialize.exe -dx Test.xml
```

<span data-ttu-id="70e4f-131">在上述兩個範例中，命令列參數中的 "x" 表示您想執行 XML SOAP 序列化。</span><span class="sxs-lookup"><span data-stu-id="70e4f-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="70e4f-132">如果在相同的位置上使用 "b"，就表示要使用二進位序列化。</span><span class="sxs-lookup"><span data-stu-id="70e4f-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="70e4f-133">如果您想嘗試序列化大量的節點，可以將主控台輸出重新導向至檔案中。</span><span class="sxs-lookup"><span data-stu-id="70e4f-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>

<span data-ttu-id="70e4f-134">例如：</span><span class="sxs-lookup"><span data-stu-id="70e4f-134">For Example:</span></span>

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

<span data-ttu-id="70e4f-135">下面幾點簡短說明了此範例所使用的類別和技術。</span><span class="sxs-lookup"><span data-stu-id="70e4f-135">The following bullets briefly describe the classes and technologies used by this sample.</span></span>

- <span data-ttu-id="70e4f-136">執行階段序列化</span><span class="sxs-lookup"><span data-stu-id="70e4f-136">Runtime Serialization</span></span>

  - <span data-ttu-id="70e4f-137"><xref:System.Runtime.Serialization.IFormatter>用來參考 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 物件。</span><span class="sxs-lookup"><span data-stu-id="70e4f-137"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>

  - <span data-ttu-id="70e4f-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>用來將連結清單序列化為二進位格式的資料流程。</span><span class="sxs-lookup"><span data-stu-id="70e4f-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="70e4f-139">二進位格式子使用的格式只有 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 型別才了解。</span><span class="sxs-lookup"><span data-stu-id="70e4f-139">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="70e4f-140">不過，資料相當簡明。</span><span class="sxs-lookup"><span data-stu-id="70e4f-140">However, the data is concise.</span></span>

  - <span data-ttu-id="70e4f-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>用來將連結清單序列化為 SOAP 格式的資料流程。</span><span class="sxs-lookup"><span data-stu-id="70e4f-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="70e4f-142">SOAP 是一種標準格式。</span><span class="sxs-lookup"><span data-stu-id="70e4f-142">SOAP is a standard format.</span></span>

- <span data-ttu-id="70e4f-143">資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="70e4f-143">Stream I/O</span></span>

  - <span data-ttu-id="70e4f-144"><xref:System.IO.Stream> 用來執行序列化及還原序列化。</span><span class="sxs-lookup"><span data-stu-id="70e4f-144"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="70e4f-145">這個範例所用的特定資料流型別是 <xref:System.IO.FileStream> 型別。</span><span class="sxs-lookup"><span data-stu-id="70e4f-145">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="70e4f-146">不過，序列化可以使用衍生自 <xref:System.IO.Stream> 的任何型別。</span><span class="sxs-lookup"><span data-stu-id="70e4f-146">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>

  - <span data-ttu-id="70e4f-147"><xref:System.IO.File> 用來建立 <xref:System.IO.FileStream> 物件，以便在磁碟上讀取及建立檔案。</span><span class="sxs-lookup"><span data-stu-id="70e4f-147"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>

  - <span data-ttu-id="70e4f-148"><xref:System.IO.FileStream> 用來將連結串列序列化及還原序列化。</span><span class="sxs-lookup"><span data-stu-id="70e4f-148"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>

## <a name="see-also"></a><span data-ttu-id="70e4f-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="70e4f-149">See also</span></span>

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
- [<span data-ttu-id="70e4f-150">基本序列化</span><span class="sxs-lookup"><span data-stu-id="70e4f-150">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="70e4f-151">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="70e4f-151">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="70e4f-152">使用屬性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="70e4f-152">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="70e4f-153">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="70e4f-153">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="70e4f-154">序列化</span><span class="sxs-lookup"><span data-stu-id="70e4f-154">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="70e4f-155">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="70e4f-155">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
