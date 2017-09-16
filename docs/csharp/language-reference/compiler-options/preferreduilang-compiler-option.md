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
# <a name="preferreduilang-c-compiler-options"></a>/preferreduilang (C# 編譯器選項)
使用 `/preferreduilang` 編譯器選項，您就可以指定 C# 編譯器顯示輸出的語言，例如錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a>引數  
 `language`  
 編譯器輸出所用語言的[語言名稱](http://go.microsoft.com/fwlink/p/?LinkId=236992)。  
  
## <a name="remarks"></a>備註  
 您可以使用 `/preferreduilang` 編譯器選項指定 C# 編譯器要用於錯誤訊息和其他命令列輸出的語言。 如果尚未安裝此語言的語言套件，則會改用作業系統的語言設定，而且不會回報錯誤。  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)

