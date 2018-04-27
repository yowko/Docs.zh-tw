---
title: 需要組件參考&#39; &lt;assemblyname&gt; &#39;包含基底類別&#39;&lt;類別名稱&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6dd53e2d0bf0535de50e465293edb26a5b1d484
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a><span data-ttu-id="7eed6-102">需要組件參考&#39; &lt;assemblyname&gt; &#39;包含基底類別&#39;&lt;類別名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="7eed6-102">Reference required to assembly &#39;&lt;assemblyname&gt;&#39; containing the base class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="7eed6-103">需要組件參考 '\<assemblyname >' 包含基底類別\<類別名稱 >'。</span><span class="sxs-lookup"><span data-stu-id="7eed6-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="7eed6-104">請在專案中加入一個參考。</span><span class="sxs-lookup"><span data-stu-id="7eed6-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="7eed6-105">此類別是在專案中未直接參考的動態連結程式庫 (DLL) 或組件中所定義。</span><span class="sxs-lookup"><span data-stu-id="7eed6-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="7eed6-106">Visual Basic 編譯器需要參考，以避免模稜兩可，如果多個 DLL 或組件中定義類別。</span><span class="sxs-lookup"><span data-stu-id="7eed6-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="7eed6-107">**錯誤 ID︰** BC30007</span><span class="sxs-lookup"><span data-stu-id="7eed6-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7eed6-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7eed6-108">To correct this error</span></span>  
  
-   <span data-ttu-id="7eed6-109">在您的專案參考中包含未參考之 DLL 或組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7eed6-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eed6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eed6-110">See Also</span></span>  
   
 [<span data-ttu-id="7eed6-111">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="7eed6-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="7eed6-112">針對中斷參考進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7eed6-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
