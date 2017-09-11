---
title: "-nowarn (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowarn
dev_langs:
- CSharp
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: 48b207fb2ecd4add0c58a38d752feb6427d943a7
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="nowarn-c-compiler-options"></a><span data-ttu-id="54c4a-102">/nowarn (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="54c4a-102">/nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="54c4a-103">**/nowarn** 選項可讓您隱藏編譯器不顯示一或多個警告。</span><span class="sxs-lookup"><span data-stu-id="54c4a-103">The **/nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="54c4a-104">請以逗點分隔多個警告編號。</span><span class="sxs-lookup"><span data-stu-id="54c4a-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c4a-105">語法</span><span class="sxs-lookup"><span data-stu-id="54c4a-105">Syntax</span></span>  
  
```console  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="54c4a-106">引數</span><span class="sxs-lookup"><span data-stu-id="54c4a-106">Arguments</span></span>  
 <span data-ttu-id="54c4a-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="54c4a-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="54c4a-108">您想要編譯器隱藏的警告編號。</span><span class="sxs-lookup"><span data-stu-id="54c4a-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54c4a-109">備註</span><span class="sxs-lookup"><span data-stu-id="54c4a-109">Remarks</span></span>  
 <span data-ttu-id="54c4a-110">您應該只要指定警告識別項的數值部分。</span><span class="sxs-lookup"><span data-stu-id="54c4a-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="54c4a-111">例如，如果您想要隱藏 CS0028，您可以指定 `/nowarn:28`。</span><span class="sxs-lookup"><span data-stu-id="54c4a-111">For example, if you want to suppress CS0028, you could specify `/nowarn:28`.</span></span>  
  
 <span data-ttu-id="54c4a-112">編譯器會以無訊息方式略過傳遞給 `/nowarn` 的警告編號，它在舊版中有效但已自編譯器移除。</span><span class="sxs-lookup"><span data-stu-id="54c4a-112">The compiler will silently ignore warning numbers passed to `/nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="54c4a-113">例如，CS0679 在 Visual Studio .NET 2002 的編譯器中有效，但後來已移除。</span><span class="sxs-lookup"><span data-stu-id="54c4a-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="54c4a-114">`/nowarn` 選項無法隱藏下列警告︰</span><span class="sxs-lookup"><span data-stu-id="54c4a-114">The following warnings cannot be suppressed by the `/nowarn` option:</span></span>  
  
-   <span data-ttu-id="54c4a-115">編譯器警告 (層級 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="54c4a-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="54c4a-116">編譯器警告 (層級 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="54c4a-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="54c4a-117">編譯器警告 (層級 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="54c4a-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="54c4a-118">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="54c4a-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="54c4a-119">開啟專案的 [屬性] **** 頁面。</span><span class="sxs-lookup"><span data-stu-id="54c4a-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="54c4a-120">如需詳細資料，請參閱[專案設計工具、建置頁 (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="54c4a-120">For details, see [Build Page, Project Designer (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="54c4a-121">按一下 [建置]**** 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="54c4a-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="54c4a-122">修改**隱藏警告**屬性。</span><span class="sxs-lookup"><span data-stu-id="54c4a-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="54c4a-123">如需如何以程式設計方式設定此編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。</span><span class="sxs-lookup"><span data-stu-id="54c4a-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c4a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54c4a-124">See Also</span></span>  
 <span data-ttu-id="54c4a-125">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="54c4a-125">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="54c4a-126"> [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="54c4a-126"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="54c4a-127"> [C# 編譯器錯誤](../../../csharp/language-reference/compiler-messages/index.md)</span><span class="sxs-lookup"><span data-stu-id="54c4a-127"> [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)</span></span>
