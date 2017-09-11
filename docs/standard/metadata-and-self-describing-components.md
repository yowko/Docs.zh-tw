---
title: "中繼資料和自我描述元件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f5469f649d594553e1567d6d611cfafcd28e2c5b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="metadata-and-self-describing-components"></a><span data-ttu-id="5d6e3-102">中繼資料和自我描述元件</span><span class="sxs-lookup"><span data-stu-id="5d6e3-102">Metadata and Self-Describing Components</span></span>
<span data-ttu-id="5d6e3-103">在過去，以一種語言撰寫的軟體元件 (.exe 或 .dll) 不容易使用以另一種語言所撰寫的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-103">In the past, a software component (.exe or .dll) that was written in one language could not easily use a software component that was written in another language.</span></span> <span data-ttu-id="5d6e3-104">COM 對這個問題提供了進一步的解決方式。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-104">COM provided a step towards solving this problem.</span></span> <span data-ttu-id="5d6e3-105">.NET Framework 允許編譯器 (Compiler) 發出額外的宣告資訊至所有模組和組件中，使元件的互通性更為容易。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-105">The .NET Framework makes component interoperation even easier by allowing compilers to emit additional declarative information into all modules and assemblies.</span></span> <span data-ttu-id="5d6e3-106">這個資訊，稱為中繼資料 (Metadata)，能幫助元件順暢地互動。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-106">This information, called metadata, helps components to interact seamlessly.</span></span>  
  
 <span data-ttu-id="5d6e3-107">中繼資料為二進位資訊，描述儲存在 Common Language Runtime 可移植執行檔 (PE) 或記憶體中的程式。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-107">Metadata is binary information describing your program that is stored either in a common language runtime portable executable (PE) file or in memory.</span></span> <span data-ttu-id="5d6e3-108">當您編譯程式碼為 PE 檔時，中繼資料被插入至檔案的一個部分，而您的程式碼則轉換至 Microsoft Intermediate Language (MSIL) 並插入至檔案的另一部分。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-108">When you compile your code into a PE file, metadata is inserted into one portion of the file, and your code is converted to Microsoft intermediate language (MSIL) and inserted into another portion of the file.</span></span> <span data-ttu-id="5d6e3-109">模組或組件中所定義和參考的一切型別和成員都描述於中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-109">Every type and member that is defined and referenced in a module or assembly is described within metadata.</span></span> <span data-ttu-id="5d6e3-110">當執行程式碼時，Runtime 載入中繼資料至記憶體中，並參考它以探索您程式碼的類別、成員、繼承 (Inheritance) 等等的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-110">When code is executed, the runtime loads metadata into memory and references it to discover information about your code's classes, members, inheritance, and so on.</span></span>  
  
 <span data-ttu-id="5d6e3-111">中繼資料會描述您程式碼中以語言中性方式定義的每一個型別和成員。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-111">Metadata describes every type and member defined in your code in a language-neutral manner.</span></span> <span data-ttu-id="5d6e3-112">中繼資料儲存下列資訊：</span><span class="sxs-lookup"><span data-stu-id="5d6e3-112">Metadata stores the following information:</span></span>  
  
-   <span data-ttu-id="5d6e3-113">組件的說明</span><span class="sxs-lookup"><span data-stu-id="5d6e3-113">Description of the assembly.</span></span>  
  
    -   <span data-ttu-id="5d6e3-114">識別 (名稱、版本、文化特性、公開金鑰)</span><span class="sxs-lookup"><span data-stu-id="5d6e3-114">Identity (name, version, culture, public key).</span></span>  
  
    -   <span data-ttu-id="5d6e3-115">匯出的型別</span><span class="sxs-lookup"><span data-stu-id="5d6e3-115">The types that are exported.</span></span>  
  
    -   <span data-ttu-id="5d6e3-116">這個組件所依存的其他組件</span><span class="sxs-lookup"><span data-stu-id="5d6e3-116">Other assemblies that this assembly depends on.</span></span>  
  
    -   <span data-ttu-id="5d6e3-117">執行所需要的安全性權限</span><span class="sxs-lookup"><span data-stu-id="5d6e3-117">Security permissions needed to run.</span></span>  
  
-   <span data-ttu-id="5d6e3-118">型別的說明</span><span class="sxs-lookup"><span data-stu-id="5d6e3-118">Description of types.</span></span>  
  
    -   <span data-ttu-id="5d6e3-119">名稱、可視性、基底類別和實作的介面</span><span class="sxs-lookup"><span data-stu-id="5d6e3-119">Name, visibility, base class, and interfaces implemented.</span></span>  
  
    -   <span data-ttu-id="5d6e3-120">成員 (方法、欄位、屬性、事件、巢狀型別)</span><span class="sxs-lookup"><span data-stu-id="5d6e3-120">Members (methods, fields, properties, events, nested types).</span></span>  
  
-   <span data-ttu-id="5d6e3-121">屬性</span><span class="sxs-lookup"><span data-stu-id="5d6e3-121">Attributes.</span></span>  
  
    -   <span data-ttu-id="5d6e3-122">修改型別和成員的額外描述項目</span><span class="sxs-lookup"><span data-stu-id="5d6e3-122">Additional descriptive elements that modify types and members.</span></span>  
  
## <a name="benefits-of-metadata"></a><span data-ttu-id="5d6e3-123">中繼資料的優點</span><span class="sxs-lookup"><span data-stu-id="5d6e3-123">Benefits of Metadata</span></span>  
 <span data-ttu-id="5d6e3-124">中繼資料是較簡單的程式撰寫模型 (Programming Model) 的關鍵，排除對介面定義語言 (IDL) 檔案、標頭檔 (Header File) 或元件參考的任何外部方法的需要。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-124">Metadata is the key to a simpler programming model, and eliminates the need for Interface Definition Language (IDL) files, header files, or any external method of component reference.</span></span> <span data-ttu-id="5d6e3-125">中繼資料可以讓 .NET Framework 語言自動以語言中性方式描述它們自己，而不讓開發人員及使用者看見。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-125">Metadata enables .NET Framework languages to describe themselves automatically in a language-neutral manner, unseen by both the developer and the user.</span></span> <span data-ttu-id="5d6e3-126">此外，中繼資料透過屬性的使用會成為可擴充的。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-126">Additionally, metadata is extensible through the use of attributes.</span></span> <span data-ttu-id="5d6e3-127">中繼資料提供下列主要好處：</span><span class="sxs-lookup"><span data-stu-id="5d6e3-127">Metadata provides the following major benefits:</span></span>  
  
-   <span data-ttu-id="5d6e3-128">自我描述檔案</span><span class="sxs-lookup"><span data-stu-id="5d6e3-128">Self-describing files.</span></span>  
  
     <span data-ttu-id="5d6e3-129">Common Language Runtime 模組和組件為自我描述的。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-129">Common language runtime modules and assemblies are self-describing.</span></span> <span data-ttu-id="5d6e3-130">模組的中繼資料包含與另一個模組互動的一切所需。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-130">A module's metadata contains everything needed to interact with another module.</span></span> <span data-ttu-id="5d6e3-131">中繼資料自動提供 COM 中的 IDL 的功能，允許您將一個檔案當做定義及實作使用。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-131">Metadata automatically provides the functionality of IDL in COM, so you can use one file for both definition and implementation.</span></span> <span data-ttu-id="5d6e3-132">Runtime 模組和組件甚至不需要向作業系統註冊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-132">Runtime modules and assemblies do not even require registration with the operating system.</span></span> <span data-ttu-id="5d6e3-133">結果，Runtime 使用的描述永遠反應您編譯檔案中的實際程式碼，這樣即增加了應用程式的可靠性。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-133">As a result, the descriptions used by the runtime always reflect the actual code in your compiled file, which increases application reliability.</span></span>  
  
-   <span data-ttu-id="5d6e3-134">語言互通性 (Interoperability) 和較容易的元件架構設計</span><span class="sxs-lookup"><span data-stu-id="5d6e3-134">Language interoperability and easier component-based design.</span></span>  
  
     <span data-ttu-id="5d6e3-135">中繼資料提供已編譯程式碼所需的全部資訊，讓您從不同語言撰寫的 PE 檔繼承類別。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-135">Metadata provides all the information required about compiled code for you to inherit a class from a PE file written in a different language.</span></span> <span data-ttu-id="5d6e3-136">您可以為任何 Managed 語言 (任何以 Common Language Runtime 為目標的語言) 所撰寫的任何類別建立執行個體，而不需擔心自訂互通性程式碼的明確封送處理 (Marshaling) 或使用。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-136">You can create an instance of any class written in any managed language (any language that targets the common language runtime) without worrying about explicit marshaling or using custom interoperability code.</span></span>  
  
-   <span data-ttu-id="5d6e3-137">屬性</span><span class="sxs-lookup"><span data-stu-id="5d6e3-137">Attributes.</span></span>  
  
     <span data-ttu-id="5d6e3-138">.NET Framework 允許您在已編譯的檔案中宣告稱為屬性的特定種類中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-138">The .NET Framework lets you declare specific kinds of metadata, called attributes, in your compiled file.</span></span> <span data-ttu-id="5d6e3-139">屬性普遍存在於 .NET Framework，並且被用來更仔細控制您程式在 Run Time 的行為。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-139">Attributes can be found throughout the .NET Framework and are used to control in more detail how your program behaves at run time.</span></span> <span data-ttu-id="5d6e3-140">此外，您可以透過使用者定義的自訂屬性，發出您自己的自訂中繼資料至 .NET Framework 檔案中。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-140">Additionally, you can emit your own custom metadata into .NET Framework files through user-defined custom attributes.</span></span> <span data-ttu-id="5d6e3-141">如需詳細資訊，請參閱[屬性](../../docs/standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-141">For more information, see [Attributes](../../docs/standard/attributes/index.md).</span></span>  
  
## <a name="metadata-and-the-pe-file-structure"></a><span data-ttu-id="5d6e3-142">中繼資料和 PE 檔結構</span><span class="sxs-lookup"><span data-stu-id="5d6e3-142">Metadata and the PE File Structure</span></span>  
 <span data-ttu-id="5d6e3-143">中繼資料是儲存在 .NET Framework 可移植執行檔 (PE) 的一個區段中，而 Microsoft Intermediate Language (MSIL) 則是儲存在 PE 檔的另一個區段。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-143">Metadata is stored in one section of a .NET Framework portable executable (PE) file, while Microsoft intermediate language (MSIL) is stored in another section of the PE file.</span></span> <span data-ttu-id="5d6e3-144">檔案的中繼資料部分包含一系列表格和堆積 (Heap) 資料結構。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-144">The metadata portion of the file contains a series of table and heap data structures.</span></span> <span data-ttu-id="5d6e3-145">MSIL 部分包含參考 PE 檔中繼資料部分的 MSIL 和中繼資料語彙基元 (Token)。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-145">The MSIL portion contains MSIL and metadata tokens that reference the metadata portion of the PE file.</span></span> <span data-ttu-id="5d6e3-146">當您使用 [MSIL 反組譯工具 (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) 等工具來檢視程式碼的 MSIL 時，可能遇到中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-146">You might encounter metadata tokens when you use tools such as the [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view your code's MSIL, for example.</span></span>  
  
### <a name="metadata-tables-and-heaps"></a><span data-ttu-id="5d6e3-147">中繼資料表和堆積</span><span class="sxs-lookup"><span data-stu-id="5d6e3-147">Metadata Tables and Heaps</span></span>  
 <span data-ttu-id="5d6e3-148">各個中繼資料表都儲存您程式項目的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-148">Each metadata table holds information about the elements of your program.</span></span> <span data-ttu-id="5d6e3-149">例如，某個中繼資料表描述您程式碼的類別，而另一個表格則描述欄位等等。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-149">For example, one metadata table describes the classes in your code, another table describes the fields, and so on.</span></span> <span data-ttu-id="5d6e3-150">如果您的程式碼中有十個類別，類別表格將會有十列，一列對應一個類別。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-150">If you have ten classes in your code, the class table will have tens rows, one for each class.</span></span> <span data-ttu-id="5d6e3-151">中繼資料表會參考其他表格和堆積。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-151">Metadata tables reference other tables and heaps.</span></span> <span data-ttu-id="5d6e3-152">例如，類別的中繼資料表會參考方法的表格。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-152">For example, the metadata table for classes references the table for methods.</span></span>  
  
 <span data-ttu-id="5d6e3-153">中繼資料也將資訊儲存在四種堆積結構中：字串、BLOB (二進位大型物件)、使用者字串和 GUID。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-153">Metadata also stores information in four heap structures: string, blob, user string, and GUID.</span></span> <span data-ttu-id="5d6e3-154">所有用於命名型別和成員的字串都儲存在字串堆積中。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-154">All the strings used to name types and members are stored in the string heap.</span></span> <span data-ttu-id="5d6e3-155">例如，方法表格不直接儲存特定方法的名稱，但指向儲存在字串堆積中的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-155">For example, a method table does not directly store the name of a particular method, but points to the method's name stored in the string heap.</span></span>  
  
### <a name="metadata-tokens"></a><span data-ttu-id="5d6e3-156">中繼資料語彙基元</span><span class="sxs-lookup"><span data-stu-id="5d6e3-156">Metadata Tokens</span></span>  
 <span data-ttu-id="5d6e3-157">各個中繼資料表的每一列在 PE 檔的 MSIL 部分由中繼資料語彙基元來唯一辨識。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-157">Each row of each metadata table is uniquely identified in the MSIL portion of the PE file by a metadata token.</span></span> <span data-ttu-id="5d6e3-158">中繼資料語彙基元在概念上類似指標，它保存 (Persist) 在 MSIL 中，並參考特定中繼資料表。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-158">Metadata tokens are conceptually similar to pointers, persisted in MSIL, that reference a particular metadata table.</span></span>  
  
 <span data-ttu-id="5d6e3-159">中繼資料語彙基元為四位元組數字。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-159">A metadata token is a four-byte number.</span></span> <span data-ttu-id="5d6e3-160">第一個位元組代表特定語彙基元所參考的中繼資料表 (方法、型別等等)。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-160">The top byte denotes the metadata table to which a particular token refers (method, type, and so on).</span></span> <span data-ttu-id="5d6e3-161">剩餘三個位元組指定中繼資料表中的列，對應正在描述的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-161">The remaining three bytes specify the row in the metadata table that corresponds to the programming element being described.</span></span> <span data-ttu-id="5d6e3-162">如果您以 C# 定義方法，並編譯它為 PE 檔，下列中繼資料語彙基元可能存在於 PE 檔的 MSIL 部分：</span><span class="sxs-lookup"><span data-stu-id="5d6e3-162">If you define a method in C# and compile it into a PE file, the following metadata token might exist in the MSIL portion of the PE file:</span></span>  
  
```  
0x06000004  
```  
  
 <span data-ttu-id="5d6e3-163">第一個位元組 (`0x06`) 表示這是 **MethodDef** 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-163">The top byte (`0x06`) indicates that this is a **MethodDef** token.</span></span> <span data-ttu-id="5d6e3-164">下面的三個位元組 (`000004`) 會告知 Common Language Runtime 到 **MethodDef** 表格的第四列來尋找說明這個方法定義的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-164">The lower three bytes (`000004`) tells the common language runtime to look in the fourth row of the **MethodDef** table for the information that describes this method definition.</span></span>  
  
### <a name="metadata-within-a-pe-file"></a><span data-ttu-id="5d6e3-165">PE 檔內的中繼資料</span><span class="sxs-lookup"><span data-stu-id="5d6e3-165">Metadata within a PE File</span></span>  
 <span data-ttu-id="5d6e3-166">當編譯 Common Language Runtime 的程式時，它被轉換至由三部分組成的 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-166">When a program is compiled for the common language runtime, it is converted to a PE file that consists of three parts.</span></span> <span data-ttu-id="5d6e3-167">下表說明各部分的內容。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-167">The following table describes the contents of each part.</span></span>  
  
|<span data-ttu-id="5d6e3-168">PE 區段</span><span class="sxs-lookup"><span data-stu-id="5d6e3-168">PE section</span></span>|<span data-ttu-id="5d6e3-169">PE 區段的內容</span><span class="sxs-lookup"><span data-stu-id="5d6e3-169">Contents of PE section</span></span>|  
|----------------|----------------------------|  
|<span data-ttu-id="5d6e3-170">PE 標頭</span><span class="sxs-lookup"><span data-stu-id="5d6e3-170">PE header</span></span>|<span data-ttu-id="5d6e3-171">PE 檔主要區段的索引和進入點 (Entry Point) 的位址。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-171">The index of the PE file's main sections and the address of the entry point.</span></span><br /><br /> <span data-ttu-id="5d6e3-172">執行階段會使用這個資訊辨識檔案為 PE 檔，並決定當載入程式至記憶體時，於何處開始執行。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-172">The runtime uses this information to identify the file as a PE file and to determine where execution starts when loading the program into memory.</span></span>|  
|<span data-ttu-id="5d6e3-173">MSIL 指令</span><span class="sxs-lookup"><span data-stu-id="5d6e3-173">MSIL instructions</span></span>|<span data-ttu-id="5d6e3-174">構成您程式碼的 Microsoft Intermediate Language 指令 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-174">The Microsoft intermediate language instructions (MSIL) that make up your code.</span></span> <span data-ttu-id="5d6e3-175">許多 MSIL 指令都有中繼資料語彙基元伴隨。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-175">Many MSIL instructions are accompanied by metadata tokens.</span></span>|  
|<span data-ttu-id="5d6e3-176">中繼資料</span><span class="sxs-lookup"><span data-stu-id="5d6e3-176">Metadata</span></span>|<span data-ttu-id="5d6e3-177">中繼資料表和堆積。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-177">Metadata tables and heaps.</span></span> <span data-ttu-id="5d6e3-178">執行階段會使用這個區段來記錄您程式碼中一切型別和成員的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-178">The runtime uses this section to record information about every type and member in your code.</span></span> <span data-ttu-id="5d6e3-179">這個區段也包括自訂屬性和安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-179">This section also includes custom attributes and security information.</span></span>|  
  
## <a name="run-time-use-of-metadata"></a><span data-ttu-id="5d6e3-180">中繼資料的執行階段使用</span><span class="sxs-lookup"><span data-stu-id="5d6e3-180">Run-Time Use of Metadata</span></span>  
 <span data-ttu-id="5d6e3-181">若要更了解中繼資料和它在 Common Language Runtime 中的角色，建構簡單程式並說明中繼資料如何影響它的執行階段存留期，可能很有幫助。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-181">To better understand metadata and its role in the common language runtime, it might be helpful to construct a simple program and illustrate how metadata affects its run-time life.</span></span> <span data-ttu-id="5d6e3-182">下列程式碼範例展示稱為 `MyApp` 的類別內的兩個方法。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-182">The following code example shows two methods inside a class called `MyApp`.</span></span> <span data-ttu-id="5d6e3-183">`Main` 方法為程式進入點，而 `Add` 方法只是傳回兩個整數引數的總和。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-183">The `Main` method is the program entry point, while the `Add` method simply returns the sum of two integer arguments.</span></span>  
  
```vb  
Public Class MyApp  
   Public Shared Sub Main()  
      Dim ValueOne As Integer = 10  
      Dim ValueTwo As Integer = 20  
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))  
   End Sub  
  
   Public Shared Function Add(One As Integer, Two As Integer) As Integer  
      Return (One + Two)  
   End Function  
End Class  
```  
  
```csharp  
using System;    
public class MyApp  
{  
   public static int Main()  
   {  
      int ValueOne = 10;  
      int ValueTwo = 20;           
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));  
      return 0;  
   }  
   public static int Add(int One, int Two)  
   {  
      return (One + Two);  
   }  
}  
```  
  
 <span data-ttu-id="5d6e3-184">當執行程式碼時，Runtime 將模組載入記憶體，並查閱中繼資料以取得這個類別。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-184">When the code runs, the runtime loads the module into memory and consults the metadata for this class.</span></span> <span data-ttu-id="5d6e3-185">一旦載入後，Runtime 會對該方法的 Microsoft Intermediate Language (MSIL) 資料流做一個廣泛的分析，以將它轉換為快速的原生機器指令。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-185">Once loaded, the runtime performs extensive analysis of the method's Microsoft intermediate language (MSIL) stream to convert it to fast native machine instructions.</span></span> <span data-ttu-id="5d6e3-186">Runtime 使用 Just-in-Time (JIT) 編譯器，按所需一次一個的方法轉換 MSIL 指令至原生機器碼 (Machine Code)。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-186">The runtime uses a just-in-time (JIT) compiler to convert the MSIL instructions to native machine code one method at a time as needed.</span></span>  
  
 <span data-ttu-id="5d6e3-187">下列範例展示從前面程式碼的 `Main` 函式產生的部分 MSIL。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-187">The following example shows part of the MSIL produced from the previous code's `Main` function.</span></span> <span data-ttu-id="5d6e3-188">您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視任何 .NET Framework 應用程式中的 MSIL 和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-188">You can view the MSIL and metadata from any .NET Framework application using the [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
```  
.entrypoint  
.maxstack  3  
.locals ([0] int32 ValueOne,  
         [1] int32 ValueTwo,  
         [2] int32 V_2,  
         [3] int32 V_3)  
IL_0000:  ldc.i4.s   10  
IL_0002:  stloc.0  
IL_0003:  ldc.i4.s   20  
IL_0005:  stloc.1  
IL_0006:  ldstr      "The Value is: {0}"  
IL_000b:  ldloc.0  
IL_000c:  ldloc.1  
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */  
```  
  
 <span data-ttu-id="5d6e3-189">JIT 編譯器會讀取整個方法的 MSIL、全面分析它，並產生那個方法的有效率的原生指令。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-189">The JIT compiler reads the MSIL for the whole method, analyzes it thoroughly, and generates efficient native instructions for the method.</span></span> <span data-ttu-id="5d6e3-190">在 `IL_000d` 上會遇到 `Add` 方法的中繼資料語彙基元 (`/*` `06000003 */`)，而執行階段即利用語彙基元查閱 **MethodDef** 表格的第三列。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-190">At `IL_000d`, a metadata token for the `Add` method (`/*` `06000003 */`) is encountered and the runtime uses the token to consult the third row of the **MethodDef** table.</span></span>  
  
 <span data-ttu-id="5d6e3-191">下表顯示 **MethodDef** 表格中，由描述 `Add` 方法的中繼資料語彙基元所參考的部分。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-191">The following table shows part of the **MethodDef** table referenced by the metadata token that describes the `Add` method.</span></span> <span data-ttu-id="5d6e3-192">雖然尚有其他中繼資料表存在於這個組件中並擁有其唯一值，但只有這個表格在討論之列。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-192">While other metadata tables exist in this assembly and have their own unique values, only this table is discussed.</span></span>  
  
|<span data-ttu-id="5d6e3-193">表格列</span><span class="sxs-lookup"><span data-stu-id="5d6e3-193">Row</span></span>|<span data-ttu-id="5d6e3-194">相關的虛擬位址 (RVA)</span><span class="sxs-lookup"><span data-stu-id="5d6e3-194">Relative Virtual Address (RVA)</span></span>|<span data-ttu-id="5d6e3-195">ImplFlags</span><span class="sxs-lookup"><span data-stu-id="5d6e3-195">ImplFlags</span></span>|<span data-ttu-id="5d6e3-196">旗標</span><span class="sxs-lookup"><span data-stu-id="5d6e3-196">Flags</span></span>|<span data-ttu-id="5d6e3-197">名稱</span><span class="sxs-lookup"><span data-stu-id="5d6e3-197">Name</span></span><br /><br /> <span data-ttu-id="5d6e3-198">(指向字串堆積)</span><span class="sxs-lookup"><span data-stu-id="5d6e3-198">(Points to string heap.)</span></span>|<span data-ttu-id="5d6e3-199">簽章 (指向 BLOB 堆積)</span><span class="sxs-lookup"><span data-stu-id="5d6e3-199">Signature (Points to blob heap.)</span></span>|  
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|  
|<span data-ttu-id="5d6e3-200">1</span><span class="sxs-lookup"><span data-stu-id="5d6e3-200">1</span></span>|<span data-ttu-id="5d6e3-201">0x00002050</span><span class="sxs-lookup"><span data-stu-id="5d6e3-201">0x00002050</span></span>|<span data-ttu-id="5d6e3-202">IL</span><span class="sxs-lookup"><span data-stu-id="5d6e3-202">IL</span></span><br /><br /> <span data-ttu-id="5d6e3-203">Managed</span><span class="sxs-lookup"><span data-stu-id="5d6e3-203">Managed</span></span>|<span data-ttu-id="5d6e3-204">Public</span><span class="sxs-lookup"><span data-stu-id="5d6e3-204">Public</span></span><br /><br /> <span data-ttu-id="5d6e3-205">ReuseSlot</span><span class="sxs-lookup"><span data-stu-id="5d6e3-205">ReuseSlot</span></span><br /><br /> <span data-ttu-id="5d6e3-206">SpecialName</span><span class="sxs-lookup"><span data-stu-id="5d6e3-206">SpecialName</span></span><br /><br /> <span data-ttu-id="5d6e3-207">RTSpecialName</span><span class="sxs-lookup"><span data-stu-id="5d6e3-207">RTSpecialName</span></span><br /><br /> <span data-ttu-id="5d6e3-208">.ctor</span><span class="sxs-lookup"><span data-stu-id="5d6e3-208">.ctor</span></span>|<span data-ttu-id="5d6e3-209">.ctor (建構函式)</span><span class="sxs-lookup"><span data-stu-id="5d6e3-209">.ctor (constructor)</span></span>||  
|<span data-ttu-id="5d6e3-210">2</span><span class="sxs-lookup"><span data-stu-id="5d6e3-210">2</span></span>|<span data-ttu-id="5d6e3-211">0x00002058</span><span class="sxs-lookup"><span data-stu-id="5d6e3-211">0x00002058</span></span>|<span data-ttu-id="5d6e3-212">IL</span><span class="sxs-lookup"><span data-stu-id="5d6e3-212">IL</span></span><br /><br /> <span data-ttu-id="5d6e3-213">Managed</span><span class="sxs-lookup"><span data-stu-id="5d6e3-213">Managed</span></span>|<span data-ttu-id="5d6e3-214">Public</span><span class="sxs-lookup"><span data-stu-id="5d6e3-214">Public</span></span><br /><br /> <span data-ttu-id="5d6e3-215">Static</span><span class="sxs-lookup"><span data-stu-id="5d6e3-215">Static</span></span><br /><br /> <span data-ttu-id="5d6e3-216">ReuseSlot</span><span class="sxs-lookup"><span data-stu-id="5d6e3-216">ReuseSlot</span></span>|<span data-ttu-id="5d6e3-217">主要</span><span class="sxs-lookup"><span data-stu-id="5d6e3-217">Main</span></span>|<span data-ttu-id="5d6e3-218">String</span><span class="sxs-lookup"><span data-stu-id="5d6e3-218">String</span></span>|  
|<span data-ttu-id="5d6e3-219">3</span><span class="sxs-lookup"><span data-stu-id="5d6e3-219">3</span></span>|<span data-ttu-id="5d6e3-220">0x0000208c</span><span class="sxs-lookup"><span data-stu-id="5d6e3-220">0x0000208c</span></span>|<span data-ttu-id="5d6e3-221">IL</span><span class="sxs-lookup"><span data-stu-id="5d6e3-221">IL</span></span><br /><br /> <span data-ttu-id="5d6e3-222">Managed</span><span class="sxs-lookup"><span data-stu-id="5d6e3-222">Managed</span></span>|<span data-ttu-id="5d6e3-223">Public</span><span class="sxs-lookup"><span data-stu-id="5d6e3-223">Public</span></span><br /><br /> <span data-ttu-id="5d6e3-224">Static</span><span class="sxs-lookup"><span data-stu-id="5d6e3-224">Static</span></span><br /><br /> <span data-ttu-id="5d6e3-225">ReuseSlot</span><span class="sxs-lookup"><span data-stu-id="5d6e3-225">ReuseSlot</span></span>|<span data-ttu-id="5d6e3-226">新增</span><span class="sxs-lookup"><span data-stu-id="5d6e3-226">Add</span></span>|<span data-ttu-id="5d6e3-227">int, int, int</span><span class="sxs-lookup"><span data-stu-id="5d6e3-227">int, int, int</span></span>|  
  
 <span data-ttu-id="5d6e3-228">表格的每一欄包含您程式碼的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-228">Each column of the table contains important information about your code.</span></span> <span data-ttu-id="5d6e3-229">**RVA** 欄允許執行階段計算定義這個方法之 MSIL 的起始記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-229">The **RVA** column allows the runtime to calculate the starting memory address of the MSIL that defines this method.</span></span> <span data-ttu-id="5d6e3-230">**ImplFlags** 和 **Flags** 欄包含描述方法的位元遮罩 (例如，方法為 Public 或 Private)。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-230">The **ImplFlags** and **Flags** columns contain bitmasks that describe the method (for example, whether the method is public or private).</span></span> <span data-ttu-id="5d6e3-231">**Name** 欄對字串堆積中的方法名稱進行索引。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-231">The **Name** column indexes the name of the method from the string heap.</span></span> <span data-ttu-id="5d6e3-232">**Signature** 欄對 Blob 堆積中方法簽章的定義進行索引。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-232">The **Signature** column indexes the definition of the method's signature in the blob heap.</span></span>  
  
 <span data-ttu-id="5d6e3-233">執行階段計算第三列中 **RVA** 欄的所需位移位址，並傳回這個位址到 JIT 編譯器，並接著進入新位址。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-233">The runtime calculates the desired offset address from the **RVA** column in the third row and returns this address to the JIT compiler, which then proceeds to the new address.</span></span> <span data-ttu-id="5d6e3-234">JIT 編譯器在新位址繼續處理 MSIL 直到遭遇另一個中繼資料語彙基元，並重複這過程。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-234">The JIT compiler continues to process MSIL at the new address until it encounters another metadata token and the process is repeated.</span></span>  
  
 <span data-ttu-id="5d6e3-235">藉著使用中繼資料，Runtime 擁有對載入您程式碼所需全部資訊的存取權，並處理它成為原生機器指令。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-235">Using metadata, the runtime has access to all the information it needs to load your code and process it into native machine instructions.</span></span> <span data-ttu-id="5d6e3-236">以這個方式，中繼資料允許自我描述檔案和連同一般型別系統的跨語言繼承。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-236">In this manner, metadata enables self-describing files and, together with the common type system, cross-language inheritance.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="5d6e3-237">相關主題</span><span class="sxs-lookup"><span data-stu-id="5d6e3-237">Related Topics</span></span>  
  
|<span data-ttu-id="5d6e3-238">標題</span><span class="sxs-lookup"><span data-stu-id="5d6e3-238">Title</span></span>|<span data-ttu-id="5d6e3-239">說明</span><span class="sxs-lookup"><span data-stu-id="5d6e3-239">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5d6e3-240">屬性</span><span class="sxs-lookup"><span data-stu-id="5d6e3-240">Attributes</span></span>](../../docs/standard/attributes/index.md)|<span data-ttu-id="5d6e3-241">描述如何套用屬性、撰寫自訂屬性和擷取儲存於屬性的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d6e3-241">Describes how to apply attributes, write custom attributes, and retrieve information that is stored in attributes.</span></span>|

