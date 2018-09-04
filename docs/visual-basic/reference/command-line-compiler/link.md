---
title: -link (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 91eba53eb8094e55af09d406515dad16fc71937d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536813"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="2f925-102">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f925-102">-link (Visual Basic)</span></span>
<span data-ttu-id="2f925-103">讓編譯器將所指定組件的 COM 類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="2f925-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f925-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f925-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f925-105">引數</span><span class="sxs-lookup"><span data-stu-id="2f925-105">Arguments</span></span>  
  
|<span data-ttu-id="2f925-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="2f925-106">Term</span></span>|<span data-ttu-id="2f925-107">定義</span><span class="sxs-lookup"><span data-stu-id="2f925-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="2f925-108">必要。</span><span class="sxs-lookup"><span data-stu-id="2f925-108">Required.</span></span> <span data-ttu-id="2f925-109">以逗號分隔的組件檔案名稱清單。</span><span class="sxs-lookup"><span data-stu-id="2f925-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2f925-110">如果檔案名稱包含空格，請用引號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="2f925-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f925-111">備註</span><span class="sxs-lookup"><span data-stu-id="2f925-111">Remarks</span></span>  
 <span data-ttu-id="2f925-112">`-link` 選項可讓您部署具有內嵌類型資訊的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f925-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="2f925-113">應用程式接著可以使用執行階段組件中實作內嵌類型資訊的類型，而不需要參考執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="2f925-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="2f925-114">如果執行階段組件有許多發行版本，包含內嵌類型資訊的應用程式不需要重新編譯，就可以搭配各種版本使用。</span><span class="sxs-lookup"><span data-stu-id="2f925-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="2f925-115">如需範例，請參閱 [Walkthrough: Embedding Types from Managed Assemblies](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) (逐步解說：從 Managed 組件內嵌類型)。</span><span class="sxs-lookup"><span data-stu-id="2f925-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="2f925-116">如果您正在使用 COM Interop，使用 `-link` 選項會特別有用。</span><span class="sxs-lookup"><span data-stu-id="2f925-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="2f925-117">您可以內嵌 COM 類型，如此一來您的應用程式就不會再要求目標電腦上必須有主要 Interop 組件 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="2f925-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="2f925-118">`-link` 選項會指示編譯器將所參考 Interop 組件的 COM 類型資訊嵌入編譯產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2f925-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="2f925-119">COM 類型是由 CLSID (GUID) 值來識別。</span><span class="sxs-lookup"><span data-stu-id="2f925-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="2f925-120">因此，應用程式可以在已安裝含相同 CLSID 值之相同 COM 類型的目標電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="2f925-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="2f925-121">自動化 Microsoft Office 的應用程式即為一個很好的例子。</span><span class="sxs-lookup"><span data-stu-id="2f925-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="2f925-122">由於 Office 等應用程式通常會在不同版本間保持相同的 CLSID 值，因此只要目標電腦上已安裝 .NET Framework 4 或更新版本，且應用程式使用包含在所參考 COM 類型中的方法、屬性或事件，應用程式就可以使用這些參考的 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="2f925-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="2f925-123">`-link` 選項只能內嵌介面、結構和委派。</span><span class="sxs-lookup"><span data-stu-id="2f925-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="2f925-124">不支援內嵌 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="2f925-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f925-125">當您在程式碼中建立內嵌 COM 類型的執行個體時，必須使用適當的介面來建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="2f925-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="2f925-126">嘗試使用 CoClass 建立內嵌 COM 類型的執行個體將會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="2f925-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="2f925-127">若要在 Visual Studio 中設定 `-link` 選項，請新增組件參考，並將 `Embed Interop Types` 屬性設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="2f925-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="2f925-128">`Embed Interop Types` 屬性的預設值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="2f925-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="2f925-129">如果您所連結的 COM 組件 (A) 本身參考另一個 COM 組件 (組件 B)，您也必須在發生下列任一情況時連結到 B 組件：</span><span class="sxs-lookup"><span data-stu-id="2f925-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="2f925-130">組件 A 的類型繼承自組件 B 的類型，或是實作組件 B 的介面。</span><span class="sxs-lookup"><span data-stu-id="2f925-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="2f925-131">所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。</span><span class="sxs-lookup"><span data-stu-id="2f925-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2f925-132">使用[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一或多個組件參考所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="2f925-132">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="2f925-133">像是[/reference](../../../visual-basic/reference/command-line-compiler/reference.md)編譯器選項`-link`編譯器選項會使用參考常用的 Vbc.rsp 回應檔[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="2f925-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies.</span></span> <span data-ttu-id="2f925-134">使用  [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)編譯器選項，如果不想讓編譯器使用 Vbc.rsp 檔案。</span><span class="sxs-lookup"><span data-stu-id="2f925-134">Use the [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="2f925-135">`-link` 的簡短形式為 `-l`。</span><span class="sxs-lookup"><span data-stu-id="2f925-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="2f925-136">泛型和內嵌類型</span><span class="sxs-lookup"><span data-stu-id="2f925-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="2f925-137">下列各節說明在內嵌 Interop 類型的應用程式中使用泛型型別時的限制。</span><span class="sxs-lookup"><span data-stu-id="2f925-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="2f925-138">泛型介面</span><span class="sxs-lookup"><span data-stu-id="2f925-138">Generic Interfaces</span></span>  
 <span data-ttu-id="2f925-139">無法使用從 Interop 組件內嵌的泛型介面。</span><span class="sxs-lookup"><span data-stu-id="2f925-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="2f925-140">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="2f925-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="2f925-141">具有泛型參數的類型</span><span class="sxs-lookup"><span data-stu-id="2f925-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="2f925-142">如果具有泛型參數的類型來自外部組件，且其參數的類型是從 Interop 組件內嵌的，則無法使用該類型。</span><span class="sxs-lookup"><span data-stu-id="2f925-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="2f925-143">這項限制不適用於介面。</span><span class="sxs-lookup"><span data-stu-id="2f925-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="2f925-144">例如，請考慮使用 <xref:Microsoft.Office.Interop.Excel> 組件中所定義的 <xref:Microsoft.Office.Interop.Excel.Range> 介面。</span><span class="sxs-lookup"><span data-stu-id="2f925-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="2f925-145">如果程式庫內嵌來自 <xref:Microsoft.Office.Interop.Excel> 組件的 Interop 類型，並公開傳回泛型型別的方法，但是此泛型型別具有類型為 <xref:Microsoft.Office.Interop.Excel.Range> 介面的參數，則該方法就必須傳回泛型介面，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="2f925-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 <span data-ttu-id="2f925-146">在下列範例中，用戶端程式碼可以呼叫傳回 <xref:System.Collections.IList> 泛型介面的方法，且不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2f925-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="2f925-147">範例</span><span class="sxs-lookup"><span data-stu-id="2f925-147">Example</span></span>  
 <span data-ttu-id="2f925-148">下列命令列編譯原始程式檔`OfficeApp.vb`，而且參考的組件`COMData1.dll`並`COMData2.dll`產生`OfficeApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="2f925-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f925-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f925-149">See Also</span></span>  
 [<span data-ttu-id="2f925-150">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="2f925-150">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2f925-151">逐步解說：從 Managed 組件內嵌類型</span><span class="sxs-lookup"><span data-stu-id="2f925-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="2f925-152">-參考 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f925-152">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="2f925-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2f925-153">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="2f925-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="2f925-154">-libpath</span></span>](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [<span data-ttu-id="2f925-155">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="2f925-155">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="2f925-156">COM Interop 簡介</span><span class="sxs-lookup"><span data-stu-id="2f925-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
