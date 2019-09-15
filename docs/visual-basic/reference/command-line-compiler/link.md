---
title: -link （Visual Basic）
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
ms.openlocfilehash: 7d68e55972336e304286e967d445f3589219b9a2
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972311"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="0f87b-102">-link （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0f87b-102">-link (Visual Basic)</span></span>
<span data-ttu-id="0f87b-103">讓編譯器將所指定組件的 COM 類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="0f87b-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f87b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f87b-104">Syntax</span></span>  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f87b-105">引數</span><span class="sxs-lookup"><span data-stu-id="0f87b-105">Arguments</span></span>  
  
|<span data-ttu-id="0f87b-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0f87b-106">Term</span></span>|<span data-ttu-id="0f87b-107">定義</span><span class="sxs-lookup"><span data-stu-id="0f87b-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="0f87b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0f87b-108">Required.</span></span> <span data-ttu-id="0f87b-109">以逗號分隔的組件檔案名稱清單。</span><span class="sxs-lookup"><span data-stu-id="0f87b-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="0f87b-110">如果檔案名稱包含空格，請用引號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="0f87b-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f87b-111">備註</span><span class="sxs-lookup"><span data-stu-id="0f87b-111">Remarks</span></span>  
 <span data-ttu-id="0f87b-112">`-link` 選項可讓您部署具有內嵌類型資訊的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f87b-112">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="0f87b-113">應用程式接著可以使用執行階段組件中實作內嵌類型資訊的類型，而不需要參考執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="0f87b-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="0f87b-114">如果執行階段組件有許多發行版本，包含內嵌類型資訊的應用程式不需要重新編譯，就可以搭配各種版本使用。</span><span class="sxs-lookup"><span data-stu-id="0f87b-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="0f87b-115">如需範例，請參閱[逐步解說：從 Managed 組件內嵌類型](../../../standard/assembly/embed-types-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="0f87b-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="0f87b-116">如果您正在使用 COM Interop，使用 `-link` 選項會特別有用。</span><span class="sxs-lookup"><span data-stu-id="0f87b-116">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="0f87b-117">您可以內嵌 COM 類型，如此一來您的應用程式就不會再要求目標電腦上必須有主要 Interop 組件 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="0f87b-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="0f87b-118">`-link` 選項會指示編譯器將所參考 Interop 組件的 COM 類型資訊嵌入編譯產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f87b-118">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="0f87b-119">COM 類型是由 CLSID (GUID) 值來識別。</span><span class="sxs-lookup"><span data-stu-id="0f87b-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="0f87b-120">因此，應用程式可以在已安裝含相同 CLSID 值之相同 COM 類型的目標電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0f87b-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="0f87b-121">自動化 Microsoft Office 的應用程式即為一個很好的例子。</span><span class="sxs-lookup"><span data-stu-id="0f87b-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="0f87b-122">由於 Office 等應用程式通常會在不同版本間保持相同的 CLSID 值，因此只要目標電腦上已安裝 .NET Framework 4 或更新版本，且應用程式使用包含在所參考 COM 類型中的方法、屬性或事件，應用程式就可以使用這些參考的 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="0f87b-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="0f87b-123">`-link` 選項只能內嵌介面、結構和委派。</span><span class="sxs-lookup"><span data-stu-id="0f87b-123">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="0f87b-124">不支援內嵌 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="0f87b-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f87b-125">當您在程式碼中建立內嵌 COM 類型的執行個體時，必須使用適當的介面來建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="0f87b-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="0f87b-126">嘗試使用 CoClass 建立內嵌 COM 類型的執行個體將會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f87b-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="0f87b-127">若要在 Visual Studio 中設定 `-link` 選項，請新增組件參考，並將 `Embed Interop Types` 屬性設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="0f87b-127">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="0f87b-128">`Embed Interop Types` 屬性的預設值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="0f87b-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="0f87b-129">如果您所連結的 COM 組件 (A) 本身參考另一個 COM 組件 (組件 B)，您也必須在發生下列任一情況時連結到 B 組件：</span><span class="sxs-lookup"><span data-stu-id="0f87b-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="0f87b-130">組件 A 的類型繼承自組件 B 的類型，或是實作組件 B 的介面。</span><span class="sxs-lookup"><span data-stu-id="0f87b-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="0f87b-131">所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。</span><span class="sxs-lookup"><span data-stu-id="0f87b-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="0f87b-132">請使用[-libpath](libpath.md)來指定您的一或多個元件參考所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="0f87b-132">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="0f87b-133">如同[/reference](reference.md)編譯器選項， `-link`編譯器選項會使用會參考常用 .NET Framework 元件的 Vbc 回應檔。</span><span class="sxs-lookup"><span data-stu-id="0f87b-133">Like the [/reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="0f87b-134">如果您不想要編譯器使用 Vbc .rsp 檔案，請使用[-noconfig](noconfig.md)編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="0f87b-134">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="0f87b-135">`-link` 的簡短形式為 `-l`。</span><span class="sxs-lookup"><span data-stu-id="0f87b-135">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="0f87b-136">泛型和內嵌類型</span><span class="sxs-lookup"><span data-stu-id="0f87b-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="0f87b-137">下列各節說明在內嵌 Interop 類型的應用程式中使用泛型型別時的限制。</span><span class="sxs-lookup"><span data-stu-id="0f87b-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="0f87b-138">泛型介面</span><span class="sxs-lookup"><span data-stu-id="0f87b-138">Generic Interfaces</span></span>  
 <span data-ttu-id="0f87b-139">無法使用從 Interop 組件內嵌的泛型介面。</span><span class="sxs-lookup"><span data-stu-id="0f87b-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="0f87b-140">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="0f87b-140">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="0f87b-141">具有泛型參數的類型</span><span class="sxs-lookup"><span data-stu-id="0f87b-141">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="0f87b-142">如果具有泛型參數的類型來自外部組件，且其參數的類型是從 Interop 組件內嵌的，則無法使用該類型。</span><span class="sxs-lookup"><span data-stu-id="0f87b-142">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="0f87b-143">這項限制不適用於介面。</span><span class="sxs-lookup"><span data-stu-id="0f87b-143">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="0f87b-144">例如，請考慮使用 <xref:Microsoft.Office.Interop.Excel> 組件中所定義的 <xref:Microsoft.Office.Interop.Excel.Range> 介面。</span><span class="sxs-lookup"><span data-stu-id="0f87b-144">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="0f87b-145">如果程式庫內嵌來自 <xref:Microsoft.Office.Interop.Excel> 組件的 Interop 類型，並公開傳回泛型型別的方法，但是此泛型型別具有類型為 <xref:Microsoft.Office.Interop.Excel.Range> 介面的參數，則該方法就必須傳回泛型介面，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="0f87b-145">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="0f87b-146">在下列範例中，用戶端程式碼可以呼叫傳回 <xref:System.Collections.IList> 泛型介面的方法，且不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f87b-146">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="0f87b-147">範例</span><span class="sxs-lookup"><span data-stu-id="0f87b-147">Example</span></span>  
 <span data-ttu-id="0f87b-148">`OfficeApp.vb`下列命令列會從`COMData1.dll`編譯原始程式檔和參考元件， `COMData2.dll`並產生`OfficeApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="0f87b-148">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f87b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f87b-149">See also</span></span>

- [<span data-ttu-id="0f87b-150">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0f87b-150">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0f87b-151">逐步解說：從受控組件內嵌類型</span><span class="sxs-lookup"><span data-stu-id="0f87b-151">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="0f87b-152">-reference （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0f87b-152">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="0f87b-153">-noconfig</span><span class="sxs-lookup"><span data-stu-id="0f87b-153">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="0f87b-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="0f87b-154">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="0f87b-155">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="0f87b-155">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="0f87b-156">COM Interop 簡介</span><span class="sxs-lookup"><span data-stu-id="0f87b-156">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
