---
title: "類型 &quot;&lt;typename&gt;&quot; 未定義 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
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
ms.openlocfilehash: 55b76e9d080a2e2e9fe6e9737a713524ea6409f6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="1ed8c-102">類型 '&lt;typename&gt;' 未定義</span><span class="sxs-lookup"><span data-stu-id="1ed8c-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="1ed8c-103">陳述式已參考未定義的型別。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="1ed8c-104">您可以定義中宣告陳述式的類型例如`Enum`， `Structure`， `Class`，或`Interface`。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="1ed8c-105">**錯誤識別碼︰** BC30002</span><span class="sxs-lookup"><span data-stu-id="1ed8c-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ed8c-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1ed8c-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1ed8c-107">請確定型別定義和它的參考都使用相同的拼字。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="1ed8c-108">確定型別定義可存取的參考。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="1ed8c-109">例如，如果型別是在另一個模組，而且已宣告`Private`、 將型別定義移至參考的模組，或將它宣告`Public`。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="1ed8c-110">請確定型別的命名空間不會重新定義您專案中。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="1ed8c-111">如果是，使用`Global`關鍵字來完整限定的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="1ed8c-112">例如，如果專案定義的命名空間，且`System`、<xref:System.Object?displayProperty=fullName>無法存取型別，除非它是以完整限定`Global`關鍵字︰ `Global.System.Object`。</xref:System.Object?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1ed8c-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=fullName> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="1ed8c-113">如果型別定義，但物件程式庫或在其中定義的型別程式庫未登錄在[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，按一下 [**加入參考**上**專案**] 功能表上，然後選取適當的物件程式庫或型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="1ed8c-114">確定為目標的.NET Framework 設定檔的一部分的組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="1ed8c-115">如需詳細資訊，請參閱[疑難排解.NET Framework 目標錯誤](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。</span><span class="sxs-lookup"><span data-stu-id="1ed8c-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed8c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ed8c-116">See Also</span></span>  
 <span data-ttu-id="1ed8c-117">[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="1ed8c-117">[Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="1ed8c-118"> [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1ed8c-118"> [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="1ed8c-119"> [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1ed8c-119"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="1ed8c-120"> [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1ed8c-120"> [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="1ed8c-121"> [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1ed8c-121"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="1ed8c-122"> [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span><span class="sxs-lookup"><span data-stu-id="1ed8c-122"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span></span>
