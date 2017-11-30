---
title: "類型 &#39;&lt;typename&gt;&#39; 未定義"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords: BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="0f6cf-102">類型 &#39;&lt;typename&gt;&#39; 未定義</span><span class="sxs-lookup"><span data-stu-id="0f6cf-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="0f6cf-103">陳述式已參考未定義的類型。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="0f6cf-104">您可以定義宣告陳述式中的類型例如`Enum`， `Structure`， `Class`，或`Interface`。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="0f6cf-105">**錯誤 ID:** BC30002</span><span class="sxs-lookup"><span data-stu-id="0f6cf-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f6cf-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="0f6cf-106">To correct this error</span></span>  
  
-   <span data-ttu-id="0f6cf-107">請確定類型定義，而且它的參考都使用相同的拼字。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="0f6cf-108">確定參考可存取的類型定義。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="0f6cf-109">例如，如果類型是在另一個模組並已宣告`Private`、 將參考的模組類型定義，或將它宣告`Public`。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="0f6cf-110">請確定型別的命名空間不在專案中重新定義。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="0f6cf-111">如果是，使用`Global`關鍵字來完整限定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="0f6cf-112">例如，如果專案定義名為的命名空間`System`、<xref:System.Object?displayProperty=nameWithType>無法存取類型，除非它是使用完整限定`Global`關鍵字： `Global.System.Object`。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="0f6cf-113">如果類型定義，但在定義的型別程式庫的物件程式庫未登錄在[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，按一下 [**加入參考**上**專案**] 功能表，然後選取適當的物件程式庫或類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="0f6cf-114">請為目標的.NET Framework 設定檔一部分的組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="0f6cf-115">如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。</span><span class="sxs-lookup"><span data-stu-id="0f6cf-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f6cf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f6cf-116">See Also</span></span>  
 [<span data-ttu-id="0f6cf-117">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="0f6cf-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="0f6cf-118">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f6cf-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="0f6cf-119">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f6cf-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="0f6cf-120">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f6cf-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="0f6cf-121">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f6cf-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="0f6cf-122">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="0f6cf-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
