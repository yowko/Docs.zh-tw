---
title: "需要組件 &#39; 的參考&lt;assemblyidentity&gt;&#39; 包含類型 &#39;&lt;typename&gt;&#39;，但找不到適合的參考，因為專案 &#39; 之間的模稜兩可&lt;projectname1&gt;&#39; 和 &#39;&lt;專案名稱 2>&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ca2454f5c306b3defd1c885dfd59ee130f3e828
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>需要組件 &#39; 的參考&lt;assemblyidentity&gt;&#39; 包含類型 &#39;&lt;typename&gt;&#39;，但找不到適合的參考，因為專案 &#39; 之間的模稜兩可&lt;projectname1&gt;&#39; 和 &#39;&lt;專案名稱 2>&gt;&#39;
運算式使用專案外部定義的類型 (例如類別、結構、介面、列舉或委派)。 不過，專案參考超過一個定義其類型的組件。  
  
 上述專案會產生具有相同名稱的組件。 因此，編譯器無法判斷要針對您正在存取的類型使用哪個組件。  
  
 若要存取另一個組件中所定義的類型， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰** BC30969  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2.  在專案屬性中，加入包含組件之檔案的參考，而這個組件定義所使用的類型。  
  
## <a name="see-also"></a>請參閱  
 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)  
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)  
 [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
