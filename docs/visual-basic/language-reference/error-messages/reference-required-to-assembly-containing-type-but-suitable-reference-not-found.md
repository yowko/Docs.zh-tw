---
title: "需要組件 &#39; 的參考&lt;assemblyidentity&gt;&#39; 包含類型 &#39;&lt;typename&gt;&#39;，但找不到適合的參考，因為專案 &#39; 之間的模稜兩可&lt;projectname1&gt;&#39; 和 &#39;&lt;專案名稱 2>&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04a1b16a10d2a3945d1efbe3a2bd0850f1da39fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="4be2f-102">需要組件 &#39; 的參考&lt;assemblyidentity&gt;&#39; 包含類型 &#39;&lt;typename&gt;&#39;，但找不到適合的參考，因為專案 &#39; 之間的模稜兩可&lt;projectname1&gt;&#39; 和 &#39;&lt;專案名稱 2>&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="4be2f-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="4be2f-103">運算式使用專案外部定義的類型 (例如類別、結構、介面、列舉或委派)。</span><span class="sxs-lookup"><span data-stu-id="4be2f-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="4be2f-104">不過，專案參考超過一個定義其類型的組件。</span><span class="sxs-lookup"><span data-stu-id="4be2f-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="4be2f-105">上述專案會產生具有相同名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="4be2f-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="4be2f-106">因此，編譯器無法判斷要針對您正在存取的類型使用哪個組件。</span><span class="sxs-lookup"><span data-stu-id="4be2f-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="4be2f-107">若要存取另一個組件中所定義的類型， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器必須有該組件的參考。</span><span class="sxs-lookup"><span data-stu-id="4be2f-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="4be2f-108">這必須是單一的明確參考，不會在專案之間造成循環參考。</span><span class="sxs-lookup"><span data-stu-id="4be2f-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="4be2f-109">**錯誤 ID︰** BC30969</span><span class="sxs-lookup"><span data-stu-id="4be2f-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4be2f-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4be2f-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="4be2f-111">決定哪些專案產生的最佳組件供專案參考。</span><span class="sxs-lookup"><span data-stu-id="4be2f-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="4be2f-112">這項決策可能會使用輕鬆存取檔案和更新頻率等準則。</span><span class="sxs-lookup"><span data-stu-id="4be2f-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="4be2f-113">在專案屬性中，加入包含組件之檔案的參考，而這個組件定義所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="4be2f-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be2f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4be2f-114">See Also</span></span>  
 [<span data-ttu-id="4be2f-115">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="4be2f-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="4be2f-116">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="4be2f-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="4be2f-117">NIB 如何：使用加入參考對話方塊以加入或移除參考</span><span class="sxs-lookup"><span data-stu-id="4be2f-117">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="4be2f-118">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="4be2f-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="4be2f-119">針對中斷參考進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="4be2f-119">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
