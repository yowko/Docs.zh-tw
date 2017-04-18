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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2692478864007c787eb19367109e6ce01882ffb1
ms.lasthandoff: 03/13/2017

---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a>需要組件參考 '&lt;assemblyname&gt;'包含基底類別'&lt;classname&gt;'
需要組件參考 '\<assemblyname >' 包含基底類別\<classname >'。 請在專案中加入一個參考。  
  
 此類別是在專案中未直接參考的動態連結程式庫 (DLL) 或組件中所定義。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器需要參考，以避免模稜兩可在多個 DLL 或組件中定義類別。  
  
 **錯誤 ID︰** BC30007  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   在您的專案參考中包含未參考之 DLL 或組件的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [針對中斷參考進行疑難排解](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)
