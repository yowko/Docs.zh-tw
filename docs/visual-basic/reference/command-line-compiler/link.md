---
title: "/link (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 71ecefc898ca37cbf7299d97518e1ce2547a58da
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="link-visual-basic"></a><span data-ttu-id="0fb6f-102">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fb6f-102">/link (Visual Basic)</span></span>
<span data-ttu-id="0fb6f-103">會導致編譯器允許您目前正在編譯的專案使用指定的組件中的 COM 型別資訊。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0fb6f-104">Syntax</span></span>  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0fb6f-105">引數</span><span class="sxs-lookup"><span data-stu-id="0fb6f-105">Arguments</span></span>  
  
|<span data-ttu-id="0fb6f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0fb6f-106">Term</span></span>|<span data-ttu-id="0fb6f-107">定義</span><span class="sxs-lookup"><span data-stu-id="0fb6f-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="0fb6f-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-108">Required.</span></span> <span data-ttu-id="0fb6f-109">組件檔案名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="0fb6f-110">如果檔案名稱包含空格，請用引號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fb6f-111">備註</span><span class="sxs-lookup"><span data-stu-id="0fb6f-111">Remarks</span></span>  
 <span data-ttu-id="0fb6f-112">`/link`選項可讓您部署應用程式包含內嵌類型資訊。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-112">The `/link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="0fb6f-113">應用程式可以使用執行階段組件中實作的內嵌的類型資訊而不需要執行階段組件的參考的型別。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="0fb6f-114">如果發佈各種執行階段組件版本，包含內嵌的類型資訊的應用程式可以使用的各種版本而不必重新編譯。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="0fb6f-115">如需範例，請參閱[逐步解說︰ 從 Managed 組件的內嵌類型](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="0fb6f-116">使用`/link`選項在您正在使用 COM interop 時會特別有用。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-116">Using the `/link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="0fb6f-117">您可以內嵌 COM 型別，使您的應用程式不再需要的主要 interop 組件 (PIA) 在目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="0fb6f-118">`/link`選項會指示編譯器將內嵌從參考的 interop 組件至產生的編譯程式碼的 COM 型別資訊。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-118">The `/link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="0fb6f-119">COM 類型的 CLSID (GUID) 值來識別。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="0fb6f-120">如此一來，您的應用程式可以在已安裝相同的 COM 型別使用相同的 CLSID 值的目標電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="0fb6f-121">Microsoft Office 自動化的應用程式都很好的例子。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="0fb6f-122">等 Office 應用程式通常會保留在不同版本的相同 CLSID 值，因為您的應用程式可以使用參照的 COM 型別，在目標電腦上安裝.NET Framework 4 或更新版本的長時間以及應用程式所使用的方法、 屬性或事件，會包含在參照 COM 型別。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="0fb6f-123">`/link`選項嵌入介面、 結構和委派。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-123">The `/link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="0fb6f-124">不支援內嵌 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fb6f-125">當您在程式碼中建立內嵌的 COM 型別的執行個體時，您必須使用適當的介面來建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="0fb6f-126">嘗試建立內嵌的 COM 型別的執行個體使用 CoClass 導致的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="0fb6f-127">若要設定`/link`選項[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]、 加入組件參考和設定`Embed Interop Types`屬性**true**。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-127">To set the `/link` option in [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="0fb6f-128">預設值為`Embed Interop Types`屬性是**false**。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="0fb6f-129">如果您連結至 COM 組件 （A） 其本身參考另一個 COM 組件 (組件 B)，您也必須連結到 B 組件，如果下列其中一種︰</span><span class="sxs-lookup"><span data-stu-id="0fb6f-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="0fb6f-130">來自組件 A 的型別繼承自型別或實作介面從 b 組件</span><span class="sxs-lookup"><span data-stu-id="0fb6f-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="0fb6f-131">欄位、 屬性、 事件或方法，從組件 B 的傳回型別或參數型別會叫用。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="0fb6f-132">使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一或多個組件參考所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-132">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="0fb6f-133">像[/參考](../../../visual-basic/reference/command-line-compiler/reference.md)編譯器選項`/link`編譯器選項會使用參考常用 Vbc.rsp 回應檔[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `/link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span></span> <span data-ttu-id="0fb6f-134">使用[/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)若不想讓編譯器使用 Vbc.rsp 檔的編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-134">Use the [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="0fb6f-135">簡短形式`/link`是`/l`。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-135">The short form of `/link` is `/l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="0fb6f-136">泛型和內嵌的類型</span><span class="sxs-lookup"><span data-stu-id="0fb6f-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="0fb6f-137">下列章節將說明在內嵌 interop 類型的應用程式中使用泛型型別限制。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="0fb6f-138">泛型介面</span><span class="sxs-lookup"><span data-stu-id="0fb6f-138">Generic Interfaces</span></span>  
 <span data-ttu-id="0fb6f-139">無法使用內嵌的 interop 組件的泛型介面。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="0fb6f-140">這在下列範例中顯示。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-140">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="0fb6f-141">[!code-vb[VbLinkCompiler #&1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0fb6f-141">[!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span></span>  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="0fb6f-142">具有泛型參數型別</span><span class="sxs-lookup"><span data-stu-id="0fb6f-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="0fb6f-143">具有泛型參數的型別內嵌的 interop 組件的類型無法使用如果類型是從外部組件。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="0fb6f-144">這項限制不適用於介面。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="0fb6f-145">例如，假設<xref:Microsoft.Office.Interop.Excel.Range>中所定義的介面<xref:Microsoft.Office.Interop.Excel>組件。</xref:Microsoft.Office.Interop.Excel> </xref:Microsoft.Office.Interop.Excel.Range></span><span class="sxs-lookup"><span data-stu-id="0fb6f-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="0fb6f-146">如果文件庫內嵌 interop 類型從<xref:Microsoft.Office.Interop.Excel>組件和型別傳回泛型型別參數的方法是的公開<xref:Microsoft.Office.Interop.Excel.Range>介面，方法必須傳回泛型介面，如下列程式碼範例所示。</xref:Microsoft.Office.Interop.Excel.Range> </xref:Microsoft.Office.Interop.Excel></span><span class="sxs-lookup"><span data-stu-id="0fb6f-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 <span data-ttu-id="0fb6f-147">[!code-vb[VbLinkCompiler #&2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0fb6f-147">[!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span></span>  
<span data-ttu-id="0fb6f-148">[!code-vb[VbLinkCompiler #&3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0fb6f-148">[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span></span>  
<span data-ttu-id="0fb6f-149">[!code-vb[VbLinkCompiler #&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="0fb6f-149">[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span></span>  
  
 <span data-ttu-id="0fb6f-150">在下列範例中，用戶端程式碼可以呼叫這個方法會傳回<xref:System.Collections.IList>泛型介面不會發生錯誤。</xref:System.Collections.IList></span><span class="sxs-lookup"><span data-stu-id="0fb6f-150">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 <span data-ttu-id="0fb6f-151">[!code-vb[VbLinkCompiler #&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="0fb6f-151">[!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fb6f-152">範例</span><span class="sxs-lookup"><span data-stu-id="0fb6f-152">Example</span></span>  
 <span data-ttu-id="0fb6f-153">下列程式碼會編譯原始程式檔`OfficeApp.vb`參考組件從`COMData1.dll`和`COMData2.dll`產生`OfficeApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="0fb6f-153">The following code compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fb6f-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fb6f-154">See Also</span></span>  
 <span data-ttu-id="0fb6f-155">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0fb6f-155">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0fb6f-156"> [逐步解說︰ 內嵌 Managed 組件的類型](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span><span class="sxs-lookup"><span data-stu-id="0fb6f-156"> [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span></span>  
<span data-ttu-id="0fb6f-157"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="0fb6f-157"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="0fb6f-158"> [/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="0fb6f-158"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="0fb6f-159"> [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) </span><span class="sxs-lookup"><span data-stu-id="0fb6f-159"> [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) </span></span>  
<span data-ttu-id="0fb6f-160"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="0fb6f-160"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="0fb6f-161"> [COM Interop 簡介](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span><span class="sxs-lookup"><span data-stu-id="0fb6f-161"> [Introduction to COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span></span>
