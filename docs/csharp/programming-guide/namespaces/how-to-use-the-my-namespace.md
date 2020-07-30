---
title: '如何使用 My 命名空間-c # 程式設計手冊'
description: 瞭解如何「我的」命名空間。 「我的」命名空間可讓您以簡單且直覺的方式存取許多 .NET 類別。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 7abd5049a979d5a15d123052cba0cfdb35bf3fb7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381706"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="4f4bf-104">如何使用 My 命名空間（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="4f4bf-104">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="4f4bf-105"><xref:Microsoft.VisualBasic.MyServices>命名空間（ `My` 在 Visual Basic 中）可讓您輕鬆且直覺地存取許多 .net 類別，讓您撰寫程式碼來與電腦、應用程式、設定、資源等等互動。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-105">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="4f4bf-106">雖然原本設計為搭配使用 Visual Basic，但 `MyServices` 命名空間可以在 C# 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-106">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="4f4bf-107">如需從 Visual Basic 中使用 `MyServices` 命名空間的詳細資訊，請參閱[使用 My 開發](../../../visual-basic/developing-apps/development-with-my/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-107">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="4f4bf-108">加入參考</span><span class="sxs-lookup"><span data-stu-id="4f4bf-108">Add a reference</span></span>

 <span data-ttu-id="4f4bf-109">您必須新增 Visual Basic 程式庫的參考，才能在您的方案中使用 `MyServices` 類別。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-109">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="4f4bf-110">將參考新增至 Visual Basic 程式庫</span><span class="sxs-lookup"><span data-stu-id="4f4bf-110">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="4f4bf-111">在**方案總管**中，以滑鼠右鍵按一下 [**參考**] 節點，然後選取 [**新增參考**]。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-111">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="4f4bf-112">當 [參考]\*\*\*\* 對話方塊出現時，向下捲動清單，然後選取 Microsoft.VisualBasic.dll。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-112">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="4f4bf-113">您也可以在程式開頭處的 `using` 區段中包含下列這行。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-113">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="4f4bf-114">範例</span><span class="sxs-lookup"><span data-stu-id="4f4bf-114">Example</span></span>  
 <span data-ttu-id="4f4bf-115">這個範例會呼叫 `MyServices` 命名空間中所包含的各種靜態方法。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-115">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="4f4bf-116">為了要編譯這個程式碼，必須將 Microsoft.VisualBasic.DLL 的參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-116">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="4f4bf-117">不是 `MyServices` 命名空間中的所有類別都可以從 C# 應用程式呼叫：例如，<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> 類別不相容。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-117">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="4f4bf-118">在此特殊情況下，可以改為使用屬於 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 的靜態方法，這些靜態方法也包含於 VisualBasic.dll 中。</span><span class="sxs-lookup"><span data-stu-id="4f4bf-118">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="4f4bf-119">例如，以下是如何使用一個這類方法來複製目錄：</span><span class="sxs-lookup"><span data-stu-id="4f4bf-119">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="4f4bf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f4bf-120">See also</span></span>

- [<span data-ttu-id="4f4bf-121">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4f4bf-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4f4bf-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="4f4bf-122">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="4f4bf-123">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="4f4bf-123">Using Namespaces</span></span>](./using-namespaces.md)
