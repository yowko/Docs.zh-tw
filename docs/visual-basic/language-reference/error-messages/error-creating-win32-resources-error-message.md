---
title: "建立 Win32 資源時發生錯誤︰&lt;錯誤訊息&gt;|Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30136
- vbc30136
dev_langs:
- VB
helpviewer_keywords:
- BC30136
ms.assetid: 05a813e4-9d65-4ce8-be8f-7ca20bbba2af
caps.latest.revision: 9
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
ms.openlocfilehash: 6ccf75a0d79f9a9f1068c2888b64b056df147078
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="error-creating-win32-resources-lterror-messagegt"></a><span data-ttu-id="b115f-102">建立 Win32 資源時發生錯誤︰&lt;錯誤訊息&gt;</span><span class="sxs-lookup"><span data-stu-id="b115f-102">Error creating Win32 resources: &lt;error message&gt;</span></span>
<span data-ttu-id="b115f-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink) 使用資訊清單產生組件。</span><span class="sxs-lookup"><span data-stu-id="b115f-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="b115f-104">連結器在建立記憶體內資源時回報了錯誤。</span><span class="sxs-lookup"><span data-stu-id="b115f-104">The linker has reported an error creating an in-memory resource.</span></span> <span data-ttu-id="b115f-105">這可能是環境問題，或是您的電腦可能記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="b115f-105">This might be a problem with the environment, or your computer might be low on memory.</span></span>  
  
 <span data-ttu-id="b115f-106">**錯誤識別碼︰** BC30136</span><span class="sxs-lookup"><span data-stu-id="b115f-106">**Error ID:** BC30136</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b115f-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b115f-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="b115f-108">檢查引用的錯誤訊息，並參考主題[Al.exe 工具錯誤和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)的進一步說明和建議。</span><span class="sxs-lookup"><span data-stu-id="b115f-108">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="b115f-109">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="b115f-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b115f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b115f-110">See Also</span></span>  
 <span data-ttu-id="b115f-111">[Al.exe （組件連結器）](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="b115f-111">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="b115f-112"> [Al.exe 工具錯誤和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span><span class="sxs-lookup"><span data-stu-id="b115f-112"> [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span></span>  
<span data-ttu-id="b115f-113"> [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="b115f-113"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
