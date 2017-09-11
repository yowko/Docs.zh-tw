---
title: "如何︰ 參考 Visual Basic 的 COM 物件 |Microsoft 文件"
ms.custom: 
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
- COM interop, referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
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
ms.openlocfilehash: 5f7f1112161d9be995cc80378ad9dd95c522198d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="2dee3-102">如何：參考 Visual Basic 的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="2dee3-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="2dee3-103">在[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，將參考加入至具有型別程式庫的 COM 物件的 COM 程式庫需要建立 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="2dee3-104">路由傳送至的 interop 組件和轉送到實際的 COM 物件參考的 COM 物件的成員。</span><span class="sxs-lookup"><span data-stu-id="2dee3-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="2dee3-105">從 COM 物件的回應會路由傳送至的 interop 組件和轉送給您[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="2dee3-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] application.</span></span>  
  
 <span data-ttu-id="2dee3-106">您可以參考的 COM 物件，而不需使用 interop 組件的.NET 組件中內嵌的 COM 物件的型別資訊。</span><span class="sxs-lookup"><span data-stu-id="2dee3-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="2dee3-107">若要內嵌類型資訊，請設定`Embed Interop Types`屬性`True`的 COM 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="2dee3-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="2dee3-108">如果您使用命令列編譯器編譯，請使用`/link`參考的 COM 程式庫的選項。</span><span class="sxs-lookup"><span data-stu-id="2dee3-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="2dee3-109">如需詳細資訊，請參閱[/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)。</span><span class="sxs-lookup"><span data-stu-id="2dee3-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2dee3-110">當您新增整合式的開發環境 (IDE) 中的型別程式庫的參考時，會自動建立 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="2dee3-111">從命令列時，您可以使用 Tlbimp 公用程式來手動建立 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="2dee3-112">將參考加入至 COM 物件</span><span class="sxs-lookup"><span data-stu-id="2dee3-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="2dee3-113">在**專案** 功能表上，選擇 **加入參考**然後按一下  **COM**對話方塊索引標籤中的。</span><span class="sxs-lookup"><span data-stu-id="2dee3-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="2dee3-114">選取您想要從清單中的 COM 物件使用的元件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="2dee3-115">若要簡化存取 interop 組件，加入`Imports`頂端的類別或模組，您將使用 COM 物件的陳述式。</span><span class="sxs-lookup"><span data-stu-id="2dee3-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="2dee3-116">例如，下列程式碼範例會匯入命名空間`INKEDLib`中參考的物件`Microsoft InkEdit Control 1.0`程式庫。</span><span class="sxs-lookup"><span data-stu-id="2dee3-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     <span data-ttu-id="2dee3-117">[!code-vb[VbVbalrInterop #&40;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2dee3-117">[!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]</span></span>  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="2dee3-118">若要建立使用 Tlbimp interop 組件</span><span class="sxs-lookup"><span data-stu-id="2dee3-118">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="2dee3-119">如果還沒有搜尋路徑的一部分，而且您目前不在其所在的目錄，則您可以加入搜尋路徑 Tlbimp 的位置。</span><span class="sxs-lookup"><span data-stu-id="2dee3-119">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="2dee3-120">呼叫 Tlbimp 從命令提示字元下，提供下列資訊︰</span><span class="sxs-lookup"><span data-stu-id="2dee3-120">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="2dee3-121">包含類型程式庫 DLL 的名稱和位置</span><span class="sxs-lookup"><span data-stu-id="2dee3-121">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="2dee3-122">名稱和命名空間的位置放置資訊</span><span class="sxs-lookup"><span data-stu-id="2dee3-122">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="2dee3-123">目標的 interop 組件的名稱和位置</span><span class="sxs-lookup"><span data-stu-id="2dee3-123">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="2dee3-124">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="2dee3-124">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="2dee3-125">您可以使用 Tlbimp 建立的型別程式庫，即使未註冊的 COM 物件的 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-125">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="2dee3-126">不過，您必須正確他們要用來在電腦上登錄 interop 組件所參考的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-126">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="2dee3-127">您可以使用 Regsvr32 公用程式隨附於 Windows 作業系統中註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-127">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dee3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dee3-128">See Also</span></span>  
 <span data-ttu-id="2dee3-129">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="2dee3-129">[COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="2dee3-130"> [Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span><span class="sxs-lookup"><span data-stu-id="2dee3-130"> [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) </span></span>  
<span data-ttu-id="2dee3-131"> [Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span><span class="sxs-lookup"><span data-stu-id="2dee3-131"> [Tlbexp.exe (Type Library Exporter)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d) </span></span>  
<span data-ttu-id="2dee3-132"> [逐步解說︰ 實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2dee3-132"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="2dee3-133"> [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span><span class="sxs-lookup"><span data-stu-id="2dee3-133"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md) </span></span>  
<span data-ttu-id="2dee3-134"> [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span><span class="sxs-lookup"><span data-stu-id="2dee3-134"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span></span>
