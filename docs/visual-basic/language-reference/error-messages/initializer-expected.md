---
title: 必須是初始設定式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46ff91ec240212571f7ec9f26e82d9d128263545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="initializer-expected"></a>必須是初始設定式
您嘗試使用物件初始設定式中的初始設定清單是空的如下列範例所示，宣告類別的執行個體。  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 至少一個欄位或屬性必須在初始設定式清單中，初始化，如下列範例所示。  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **錯誤 ID:** BC30996  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  初始化至少一個欄位或屬性初始設定式，或請勿使用物件初始設定式。  
  
## <a name="see-also"></a>另請參閱  
 [物件初始設定式：具名和匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [如何：使用物件初始設定式宣告物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
