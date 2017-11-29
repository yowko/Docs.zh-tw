---
title: "需要組件 &#39; 的參考&lt;assemblyname&gt;&#39; 包含基底類別 &#39;&lt;classname&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords: BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7413c82a9c61d13e7ca6fa18f27a4769a0937f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a>需要組件 &#39; 的參考&lt;assemblyname&gt;&#39; 包含基底類別 &#39;&lt;classname&gt;&#39;
需要組件參考 '\<assemblyname >' 包含基底類別\<類別名稱 >'。 請在專案中加入一個參考。  
  
 此類別是在專案中未直接參考的動態連結程式庫 (DLL) 或組件中所定義。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器需要參考，以避免當類別在多個 DLL 或組件中定義時所發生的模稜兩可情況。  
  
 **錯誤 ID︰** BC30007  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   在您的專案參考中包含未參考之 DLL 或組件的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)  
 [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
