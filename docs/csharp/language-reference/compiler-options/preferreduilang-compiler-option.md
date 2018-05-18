---
title: -preferreduilang (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 21a3baceb8a46723de1c633e415af0660bb41840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# 編譯器選項)
使用 `-preferreduilang` 編譯器選項，您就可以指定 C# 編譯器顯示輸出的語言，例如錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>引數  
 `language`  
 編譯器輸出所用語言的[語言名稱](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx)。  
  
## <a name="remarks"></a>備註  
 您可以使用 `-preferreduilang` 編譯器選項指定 C# 編譯器要用於錯誤訊息和其他命令列輸出的語言。 如果尚未安裝此語言的語言套件，則會改用作業系統的語言設定，而且不會回報錯誤。  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
