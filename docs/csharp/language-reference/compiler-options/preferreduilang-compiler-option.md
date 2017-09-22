---
title: "-preferreduilang (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /preferreduilang
dev_langs:
- CSharp
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b94c2794642ad93a78eaafdeb655310e4ecb2d25
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# /preferreduilang (C# Compiler Options)
使用 `/preferreduilang` 編譯器選項，您可以指定 C\# 編譯器顯示輸出的語言，例如錯誤訊息。  
  
## 語法  
  
```  
/preferreduilang: language  
```  
  
## Arguments  
 `language`  
 為編譯器輸出所使用的語言之[語言名稱](http://go.microsoft.com/fwlink/p/?LinkId=236992) 。  
  
## 備註  
 您可以使用 `/preferreduilang` 編譯器選項來指定 C\# 編譯器的錯誤訊息和其他命令列輸出使用的語言。  如果未安裝此語言的語言套件，則改用作業系統的語言設定，不會回報錯誤。  
  
```c#  
csc.exe /preferreduilang:ja-JP  
```  
  
## 需求  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)

