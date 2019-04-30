---
title: 需要組件 '<assemblyidentity>' (包含類型 '<typename>') 的參考，但是由於專案 '<projectname1>' 和 '<projectname2>' 之間模稜兩可，所以找不到適合的參考
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 9868598b32ae17ef5bfb5dd738f8a7541515f5ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013742"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="c8a35-102">需要組件參考 '\<組件識別 >' 包含類型'\<類型名稱 >'，但找不到適合的參考，因為專案之間的模稜兩可\<projectname1 >' 和 '\<專案名稱 2> >'</span><span class="sxs-lookup"><span data-stu-id="c8a35-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>
<span data-ttu-id="c8a35-103">運算式使用專案外部定義的類型 (例如類別、結構、介面、列舉或委派)。</span><span class="sxs-lookup"><span data-stu-id="c8a35-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="c8a35-104">不過，專案參考超過一個定義其類型的組件。</span><span class="sxs-lookup"><span data-stu-id="c8a35-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="c8a35-105">上述專案會產生具有相同名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="c8a35-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="c8a35-106">因此，編譯器無法判斷要針對您正在存取的類型使用哪個組件。</span><span class="sxs-lookup"><span data-stu-id="c8a35-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="c8a35-107">若要存取另一個組件中定義的類型，Visual Basic 編譯器必須有該組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c8a35-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="c8a35-108">這必須是單一的明確參考，不會在專案之間造成循環參考。</span><span class="sxs-lookup"><span data-stu-id="c8a35-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="c8a35-109">**錯誤 ID:** BC30969</span><span class="sxs-lookup"><span data-stu-id="c8a35-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8a35-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c8a35-110">To correct this error</span></span>  
  
1. <span data-ttu-id="c8a35-111">決定哪些專案產生的最佳組件供專案參考。</span><span class="sxs-lookup"><span data-stu-id="c8a35-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="c8a35-112">這項決策可能會使用輕鬆存取檔案和更新頻率等準則。</span><span class="sxs-lookup"><span data-stu-id="c8a35-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="c8a35-113">在專案屬性中，加入包含組件之檔案的參考，而這個組件定義所使用的類型。</span><span class="sxs-lookup"><span data-stu-id="c8a35-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a35-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8a35-114">See also</span></span>

- [<span data-ttu-id="c8a35-115">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="c8a35-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="c8a35-116">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="c8a35-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="c8a35-117">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="c8a35-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="c8a35-118">針對中斷參考進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c8a35-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
