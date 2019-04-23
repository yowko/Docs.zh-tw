---
title: HOW TO：使用 My 命名空間 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 9621f6a01ef4e30bf34b97df3d2c3033e9b62a23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316020"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="fc78c-102">HOW TO：使用 My 命名空間 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="fc78c-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="fc78c-103"><xref:Microsoft.VisualBasic.MyServices> 命名空間 (Visual Basic 中的 `My`) 允許您以輕鬆且直覺式的方式存取許多 .NET Framework 類別，讓您能夠撰寫程式碼以與電腦、應用程式、設定、資源等等互動。</span><span class="sxs-lookup"><span data-stu-id="fc78c-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="fc78c-104">雖然原本設計為搭配使用 Visual Basic，但 `MyServices` 命名空間可以在 C# 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="fc78c-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="fc78c-105">如需從 Visual Basic 中使用 `MyServices` 命名空間的詳細資訊，請參閱[使用 My 開發](../../../visual-basic/developing-apps/development-with-my/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fc78c-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="fc78c-106">新增參考</span><span class="sxs-lookup"><span data-stu-id="fc78c-106">Adding a Reference</span></span>  
 <span data-ttu-id="fc78c-107">您必須新增 Visual Basic 程式庫的參考，才能在您的方案中使用 `MyServices` 類別。</span><span class="sxs-lookup"><span data-stu-id="fc78c-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="fc78c-108">新增 Visual Basic 程式庫的參考</span><span class="sxs-lookup"><span data-stu-id="fc78c-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="fc78c-109">在方案總管 中，以滑鼠右鍵按一下 [參考] 節點，然後選取 [Add Reference] (新增參考)。</span><span class="sxs-lookup"><span data-stu-id="fc78c-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="fc78c-110">當 [參考] 對話方塊出現時，向下捲動清單，然後選取 Microsoft.VisualBasic.dll。</span><span class="sxs-lookup"><span data-stu-id="fc78c-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="fc78c-111">您也可以在程式開頭處的 `using` 區段中包含下列這行。</span><span class="sxs-lookup"><span data-stu-id="fc78c-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="fc78c-112">範例</span><span class="sxs-lookup"><span data-stu-id="fc78c-112">Example</span></span>  
 <span data-ttu-id="fc78c-113">這個範例會呼叫 `MyServices` 命名空間中所包含的各種靜態方法。</span><span class="sxs-lookup"><span data-stu-id="fc78c-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="fc78c-114">為了要編譯這個程式碼，必須將 Microsoft.VisualBasic.DLL 的參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="fc78c-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="fc78c-115">不是 `MyServices` 命名空間中的所有類別都可以從 C# 應用程式呼叫：例如，<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> 類別不相容。</span><span class="sxs-lookup"><span data-stu-id="fc78c-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="fc78c-116">在此特殊情況下，可以改為使用屬於 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 的靜態方法，這些靜態方法也包含於 VisualBasic.dll 中。</span><span class="sxs-lookup"><span data-stu-id="fc78c-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="fc78c-117">例如，以下是如何使用一個這類方法來複製目錄：</span><span class="sxs-lookup"><span data-stu-id="fc78c-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="fc78c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc78c-118">See also</span></span>

- [<span data-ttu-id="fc78c-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fc78c-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fc78c-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="fc78c-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="fc78c-121">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="fc78c-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
