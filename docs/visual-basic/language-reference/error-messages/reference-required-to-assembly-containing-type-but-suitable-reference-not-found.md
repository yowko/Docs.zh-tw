---
title: "需要組件參考 &quot;&lt;assemblyidentity&gt;&quot;包含型別&quot;&lt;typename&gt;&quot;，但是由於專案之間的模稜兩可而找不到適合的參考&lt;projectname1&gt;&quot;和&quot;&lt;projectname2&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
dev_langs:
- VB
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
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
ms.openlocfilehash: 38f016b9d0de053c9a95a6d4a4d810d55af903e9
ms.lasthandoff: 03/13/2017

---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>需要組件參考 '&lt;assemblyidentity&gt;'包含型別'&lt;typename&gt;'，但是由於專案之間的模稜兩可而找不到適合的參考&lt;projectname1&gt;'和'&lt;projectname2&gt;'
運算式使用專案外部定義的類型 (例如類別、結構、介面、列舉或委派)。 不過，專案參考超過一個定義其類型的組件。  
  
 上述專案會產生具有相同名稱的組件。 因此，編譯器無法判斷要針對您正在存取的類型使用哪個組件。  
  
 若要存取其他的組件中定義的型別[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰** BC30969  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之檔案的參考，而這個組件定義所使用的類型。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [宣告項目參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 如何︰ 修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [針對中斷參考進行疑難排解](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)
