---
title: 類型&#39; &lt;typename&gt; &#39;未定義
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 8e303a9ac6529fbbc818c94497a16463897fb0c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496123"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="7dd16-102">類型&#39; &lt;typename&gt; &#39;未定義</span><span class="sxs-lookup"><span data-stu-id="7dd16-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="7dd16-103">陳述式已參考了尚未定義的類型。</span><span class="sxs-lookup"><span data-stu-id="7dd16-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="7dd16-104">您可以定義在宣告陳述式類型這類`Enum`， `Structure`， `Class`，或`Interface`。</span><span class="sxs-lookup"><span data-stu-id="7dd16-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="7dd16-105">**錯誤 ID:** BC30002</span><span class="sxs-lookup"><span data-stu-id="7dd16-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7dd16-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7dd16-106">To correct this error</span></span>  
  
-   <span data-ttu-id="7dd16-107">請確定類型定義，而且它的參考都使用相同的拼字。</span><span class="sxs-lookup"><span data-stu-id="7dd16-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="7dd16-108">確定存取參考的型別定義。</span><span class="sxs-lookup"><span data-stu-id="7dd16-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="7dd16-109">例如，如果類型是在另一個模組，而且已宣告`Private`、 將型別定義移至參考的模組，或將它宣告`Public`。</span><span class="sxs-lookup"><span data-stu-id="7dd16-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="7dd16-110">請確定類型的命名空間不會重新定義您的專案內。</span><span class="sxs-lookup"><span data-stu-id="7dd16-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="7dd16-111">如果是，使用`Global`關鍵字來完整限定的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7dd16-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="7dd16-112">例如，如果專案定義名為命名空間`System`，則<xref:System.Object?displayProperty=nameWithType>無法存取類型，除非它是以完整限定`Global`關鍵字： `Global.System.Object`。</span><span class="sxs-lookup"><span data-stu-id="7dd16-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="7dd16-113">如果類型定義，但在 Visual Basic 中，按一下的物件程式庫或在其中定義的型別程式庫未註冊**加入參考**上**專案**功能表、，然後選取適當的物件程式庫或型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="7dd16-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="7dd16-114">請確定類型位於組件的目標.NET Framework 設定檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="7dd16-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="7dd16-115">如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。</span><span class="sxs-lookup"><span data-stu-id="7dd16-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd16-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dd16-116">See also</span></span>
- [<span data-ttu-id="7dd16-117">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="7dd16-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="7dd16-118">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="7dd16-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="7dd16-119">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="7dd16-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="7dd16-120">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="7dd16-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="7dd16-121">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="7dd16-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="7dd16-122">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="7dd16-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
