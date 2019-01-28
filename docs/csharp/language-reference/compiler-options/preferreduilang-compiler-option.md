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
ms.openlocfilehash: d079441e91ff90bcc974564bbd7069e0548a7d77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575282"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# 編譯器選項)
使用 `-preferreduilang` 編譯器選項，您就可以指定 C# 編譯器顯示輸出的語言，例如錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>引數  
 `language`  
 編譯器輸出所用語言的[語言名稱](/windows/desktop/Intl/language-names)。  
  
## <a name="remarks"></a>備註  
 您可以使用 `-preferreduilang` 編譯器選項指定 C# 編譯器要用於錯誤訊息和其他命令列輸出的語言。 如果尚未安裝此語言的語言套件，則會改用作業系統的語言設定，而且不會回報錯誤。  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
