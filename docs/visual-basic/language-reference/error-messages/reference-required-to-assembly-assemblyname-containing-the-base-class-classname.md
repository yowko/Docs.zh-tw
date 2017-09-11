---
title: "需要組件參考 &quot;&lt;assemblyname&gt;&quot;包含基底類別&quot;&lt;classname&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30007
- vbc30007
dev_langs:
- VB
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 131f8fd53fe025ac16450d9ff0019626444c6cc6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a><span data-ttu-id="d22ef-102">需要組件參考 '&lt;assemblyname&gt;'包含基底類別'&lt;classname&gt;'</span><span class="sxs-lookup"><span data-stu-id="d22ef-102">Reference required to assembly &#39;&lt;assemblyname&gt;&#39; containing the base class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="d22ef-103">需要組件參考 '\<assemblyname >' 包含基底類別\<classname >'。</span><span class="sxs-lookup"><span data-stu-id="d22ef-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="d22ef-104">請在專案中加入一個參考。</span><span class="sxs-lookup"><span data-stu-id="d22ef-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="d22ef-105">此類別是在專案中未直接參考的動態連結程式庫 (DLL) 或組件中所定義。</span><span class="sxs-lookup"><span data-stu-id="d22ef-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="d22ef-106">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器需要參考，以避免模稜兩可在多個 DLL 或組件中定義類別。</span><span class="sxs-lookup"><span data-stu-id="d22ef-106">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="d22ef-107">**錯誤 ID︰** BC30007</span><span class="sxs-lookup"><span data-stu-id="d22ef-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d22ef-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d22ef-108">To correct this error</span></span>  
  
-   <span data-ttu-id="d22ef-109">在您的專案參考中包含未參考之 DLL 或組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d22ef-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22ef-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d22ef-110">See Also</span></span>  
 <span data-ttu-id="d22ef-111">[NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="d22ef-111">[NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="d22ef-112"> [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="d22ef-112"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="d22ef-113"> [針對中斷參考進行疑難排解](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span><span class="sxs-lookup"><span data-stu-id="d22ef-113"> [Troubleshooting Broken References](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span></span>
