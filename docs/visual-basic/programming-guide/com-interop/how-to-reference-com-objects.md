---
title: "如何：參考 Visual Basic 的 COM 物件"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a8ac167b40688b1d1116f148d0d5fd6afdcaada8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="2f26d-102">如何：參考 Visual Basic 的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="2f26d-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="2f26d-103">在[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，將參考加入至具有型別程式庫的 COM 物件的 COM 程式庫需要建立 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="2f26d-104">COM 物件的成員的參考會路由傳送至的 interop 組件，接著再轉寄到實際的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="2f26d-105">從 COM 物件的回應會路由傳送至的 interop 組件，並轉送至您[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f26d-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="2f26d-106">您可以參考 COM 物件，而不使用 interop 組件是.NET 組件中內嵌的 COM 物件的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="2f26d-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="2f26d-107">若要將內嵌類型資訊，請設定`Embed Interop Types`屬性`True`的 COM 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="2f26d-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="2f26d-108">如果您正在使用命令列編譯器來編譯，請使用`/link`參考的 COM 程式庫的選項。</span><span class="sxs-lookup"><span data-stu-id="2f26d-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="2f26d-109">如需詳細資訊，請參閱[/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)。</span><span class="sxs-lookup"><span data-stu-id="2f26d-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="2f26d-110">當您新增整合式的開發環境 (IDE) 中的類型程式庫的參考時，會自動建立 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="2f26d-111">從命令列時，您可以使用 Tlbimp 公用程式來手動建立 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="2f26d-112">將參考加入至 COM 物件</span><span class="sxs-lookup"><span data-stu-id="2f26d-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="2f26d-113">在**專案**功能表上，選擇**加入參考**，然後按一下  **COM**對話方塊索引標籤中的。</span><span class="sxs-lookup"><span data-stu-id="2f26d-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="2f26d-114">選取您想要從清單中的 COM 物件使用的元件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="2f26d-115">若要簡化的存取權的 interop 組件，加入`Imports`頂端的類別或模組中，您會使用 COM 物件的陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f26d-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="2f26d-116">例如，下列程式碼範例會匯入命名空間`INKEDLib`中參考的物件`Microsoft InkEdit Control 1.0`程式庫。</span><span class="sxs-lookup"><span data-stu-id="2f26d-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="2f26d-117">若要建立使用 Tlbimp interop 組件</span><span class="sxs-lookup"><span data-stu-id="2f26d-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="2f26d-118">如果還沒有的搜尋路徑的一部分，而且您目前不在其所在的目錄，加入搜尋路徑 Tlbimp 的位置。</span><span class="sxs-lookup"><span data-stu-id="2f26d-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="2f26d-119">呼叫 Tlbimp 從命令提示字元，提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="2f26d-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="2f26d-120">包含型別程式庫的 DLL 的名稱和位置</span><span class="sxs-lookup"><span data-stu-id="2f26d-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="2f26d-121">名稱和命名空間的位置資訊放置的位置</span><span class="sxs-lookup"><span data-stu-id="2f26d-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="2f26d-122">目標的 interop 組件的名稱和位置</span><span class="sxs-lookup"><span data-stu-id="2f26d-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="2f26d-123">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="2f26d-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="2f26d-124">您可以使用 Tlbimp 建立 interop 組件的類型程式庫，即使未註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="2f26d-125">不過，您必須正確他們要用來在電腦上註冊 interop 組件所參考的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="2f26d-126">您可以使用 Regsvr32 公用程式隨附於 Windows 作業系統中註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="2f26d-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f26d-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f26d-127">See Also</span></span>  
 [<span data-ttu-id="2f26d-128">COM Interop</span><span class="sxs-lookup"><span data-stu-id="2f26d-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="2f26d-129">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="2f26d-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="2f26d-130">Tlbexp.exe (類型程式庫匯出工具)</span><span class="sxs-lookup"><span data-stu-id="2f26d-130">Tlbexp.exe (Type Library Exporter)</span></span>](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [<span data-ttu-id="2f26d-131">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="2f26d-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="2f26d-132">互通性的疑難排解</span><span class="sxs-lookup"><span data-stu-id="2f26d-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [<span data-ttu-id="2f26d-133">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="2f26d-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
