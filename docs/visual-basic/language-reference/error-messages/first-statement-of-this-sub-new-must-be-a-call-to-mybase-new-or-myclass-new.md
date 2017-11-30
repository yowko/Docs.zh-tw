---
title: "這 &#39; 第一個陳述式新的子 &#39;必須呼叫 &#39;MyBase.New &#39;或 &#39;MyClass.New &#39;（沒有可存取建構函式不含參數）"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords: BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1065643e1f6c868092fbad839af0dbbd33afaf01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>這 &#39; 第一個陳述式新的子 &#39;必須呼叫 &#39;MyBase.New &#39;或 &#39;MyClass.New &#39;（沒有可存取建構函式不含參數）
這個 'Sub New' 的第一個陳述式必須呼叫 'MyBase.New' 或 'MyClass.New'，因為基底類別\<basename >' 的'\<derivedname >' 沒有可存取 ' Sub New' 可呼叫沒有引數。  
  
 在衍生類別中，每個建構函式必須呼叫基底類別建構函式 (`MyBase.New`)。 如果基底類別的建構函式不含任何參數是在衍生類別，可存取`MyBase.New`可以自動呼叫。 如果不是，呼叫基底類別建構函式必須有參數，並無法自動完成。 在此情況下，每個衍生的類別建構函式的第一個陳述式必須呼叫基底類別中，參數化建構函式或呼叫其他建構函式呼叫的基底類別建構函式可讓衍生類別中。  
  
 **錯誤 ID:** BC30148  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   呼叫`MyBase.New`提供必要的參數，或呼叫這類呼叫的對等建構函式。  
  
     例如，如果基底類別建構函式宣告為`Public Sub New(ByVal index as Integer)`、 第一個陳述式在衍生類別建構函式可能`MyBase.New(100)`。  
  
## <a name="see-also"></a>另請參閱  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
