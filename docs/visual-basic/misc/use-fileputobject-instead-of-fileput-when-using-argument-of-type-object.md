---
title: "使用 &#39;FilePutObject &#39;而不是 &#39;FilePut &#39;類型 &#39; 物件 &#39; 的引數時"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>使用 &#39;FilePutObject &#39;而不是 &#39;FilePut &#39;類型 &#39; 物件 &#39; 的引數時
`FilePut`方法包含類型的引數`Object`。 `FilePutObject` 應該用於取代 `FilePut` ，以避免模稜兩可。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將 `FilePut` 取代為 `FilePutObject`。  
  
-   請將 `Object` 引數轉換為更特定的類型。  
  
-   使用 `My.Computer.FileSystem` 物件中可用的功能。  
  
## <a name="see-also"></a>另請參閱  
 [不在組建中： FilePutObject 函式](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [My.Computer.FileSystem 物件](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [My.Computer.FileSystem.WriteAllBytes 方法](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
