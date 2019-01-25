---
title: 需要組件參考&#39; &lt;assemblyname&gt; &#39;包含的基底類別&#39; &lt;classname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: f2aa8f1f05ce15bd25992b7f1851854952108813
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506262"
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a><span data-ttu-id="b47fd-102">需要組件參考&#39; &lt;assemblyname&gt; &#39;包含的基底類別&#39; &lt;classname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="b47fd-102">Reference required to assembly &#39;&lt;assemblyname&gt;&#39; containing the base class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="b47fd-103">需要組件參考 '\<組件名稱 >' 包含基底類別\<類別名稱 >'。</span><span class="sxs-lookup"><span data-stu-id="b47fd-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="b47fd-104">請在專案中加入一個參考。</span><span class="sxs-lookup"><span data-stu-id="b47fd-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="b47fd-105">此類別是在專案中未直接參考的動態連結程式庫 (DLL) 或組件中所定義。</span><span class="sxs-lookup"><span data-stu-id="b47fd-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="b47fd-106">Visual Basic 編譯器需要參考，以避免模稜兩可，以防多個 DLL 或組件中定義類別。</span><span class="sxs-lookup"><span data-stu-id="b47fd-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="b47fd-107">**錯誤 ID:** BC30007</span><span class="sxs-lookup"><span data-stu-id="b47fd-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b47fd-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b47fd-108">To correct this error</span></span>  
  
-   <span data-ttu-id="b47fd-109">在您的專案參考中包含未參考之 DLL 或組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b47fd-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47fd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b47fd-110">See also</span></span>

- [<span data-ttu-id="b47fd-111">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="b47fd-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="b47fd-112">針對中斷參考進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b47fd-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
