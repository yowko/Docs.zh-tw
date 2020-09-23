---
title: 如何：參考 Visual Basic 的 COM 物件
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 43ba068663db9f8c3816a6f731395a6682a130e6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083289"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="4af4e-102">如何：參考 Visual Basic 的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="4af4e-102">How to: Reference COM Objects from Visual Basic</span></span>

<span data-ttu-id="4af4e-103">在 Visual Basic 中，加入具有類型程式庫之 COM 物件的參考需要建立 COM 程式庫的 interop 元件。</span><span class="sxs-lookup"><span data-stu-id="4af4e-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="4af4e-104">COM 物件成員的參考會路由至 interop 元件，然後轉送至實際的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="4af4e-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="4af4e-105">來自 COM 物件的回應會路由傳送至 interop 元件，並轉送至您的 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4af4e-105">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="4af4e-106">您可以在 .NET 元件中內嵌 COM 物件的型別資訊，而不使用 interop 元件來參考 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="4af4e-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="4af4e-107">若要內嵌型別資訊，請將的屬性設定為，以便 `Embed Interop Types` `True` 參考 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="4af4e-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="4af4e-108">如果您要使用命令列編譯器進行編譯，請使用 `/link` 選項來參考 COM 程式庫。</span><span class="sxs-lookup"><span data-stu-id="4af4e-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="4af4e-109">如需詳細資訊，請參閱 [-連結 (Visual Basic) ](../../reference/command-line-compiler/link.md)。</span><span class="sxs-lookup"><span data-stu-id="4af4e-109">For more information, see [-link (Visual Basic)](../../reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="4af4e-110">當您從整合式開發環境中加入類型程式庫的參考時，Visual Basic 會自動建立 interop 元件 (IDE) 。</span><span class="sxs-lookup"><span data-stu-id="4af4e-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="4af4e-111">從命令列工作時，您可以使用 Tlbimp.exe 公用程式手動建立 interop 元件。</span><span class="sxs-lookup"><span data-stu-id="4af4e-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="4af4e-112">若要加入 COM 物件的參考</span><span class="sxs-lookup"><span data-stu-id="4af4e-112">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="4af4e-113">在 [ **專案** ] 功能表上，選擇 [ **加入參考** ]，然後按一下對話方塊中的 [ **COM** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4af4e-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="4af4e-114">從 COM 物件清單中選取您要使用的元件。</span><span class="sxs-lookup"><span data-stu-id="4af4e-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="4af4e-115">若要簡化 interop 元件的存取，請將 `Imports` 語句加入至您將在其中使用 COM 物件的類別或模組的頂端。</span><span class="sxs-lookup"><span data-stu-id="4af4e-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="4af4e-116">例如，下列程式碼範例會匯入連結 `INKEDLib` 庫中所參考之物件的命名空間 `Microsoft InkEdit Control 1.0` 。</span><span class="sxs-lookup"><span data-stu-id="4af4e-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="4af4e-117">若要使用 Tlbimp.exe 建立 interop 元件</span><span class="sxs-lookup"><span data-stu-id="4af4e-117">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="4af4e-118">將 Tlbimp.exe 的位置新增至搜尋路徑，如果它還不是搜尋路徑的一部分，而且您目前不在它所在的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4af4e-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="4af4e-119">從命令提示字元呼叫 Tlbimp.exe，提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="4af4e-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="4af4e-120">包含類型程式庫之 DLL 的名稱和位置</span><span class="sxs-lookup"><span data-stu-id="4af4e-120">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="4af4e-121">應放置資訊的命名空間名稱和位置</span><span class="sxs-lookup"><span data-stu-id="4af4e-121">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="4af4e-122">目標 interop 元件的名稱和位置</span><span class="sxs-lookup"><span data-stu-id="4af4e-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="4af4e-123">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="4af4e-123">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="4af4e-124">您可以使用 Tlbimp.exe 來建立類型程式庫的 interop 元件，即使是未註冊的 COM 物件也是如此。</span><span class="sxs-lookup"><span data-stu-id="4af4e-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="4af4e-125">不過，interop 元件所參考的 COM 物件必須在要使用的電腦上正確註冊。</span><span class="sxs-lookup"><span data-stu-id="4af4e-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="4af4e-126">您可以使用 Windows 作業系統隨附的 Regsvr32 公用程式來註冊 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="4af4e-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af4e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4af4e-127">See also</span></span>

- [<span data-ttu-id="4af4e-128">COM Interop</span><span class="sxs-lookup"><span data-stu-id="4af4e-128">COM Interop</span></span>](index.md)
- [<span data-ttu-id="4af4e-129">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="4af4e-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="4af4e-130">Tlbexp.exe (類型程式庫匯出工具)</span><span class="sxs-lookup"><span data-stu-id="4af4e-130">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="4af4e-131">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="4af4e-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="4af4e-132">疑難排解互通性的問題</span><span class="sxs-lookup"><span data-stu-id="4af4e-132">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
- [<span data-ttu-id="4af4e-133">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="4af4e-133">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
