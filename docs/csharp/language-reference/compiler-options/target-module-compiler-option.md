---
title: -target:module (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602437"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:module (C# 編譯器選項)
這個選項可讓編譯器不要產生組件資訊清單。  
  
## <a name="syntax"></a>語法  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>備註  
 根據預設，使用這個選項編譯時，所建立的輸出檔副檔名會是 .netmodule。  
  
 .NET Framework Common Language Runtime 無法載入沒有組件資訊清單的檔案。 不過，這類檔案可以透過 [-addmodule](./addmodule-compiler-option.md) 併入組件的組件資訊清單。  
  
 如果在單一編譯中建立多個模組，則編譯中的其他模組可以使用某個模組中的 [internal](../keywords/internal.md) 類型。 某個模組中的程式碼參考另一個模組中的 `internal` 類型時，必須透過 **-addmodule** 將這兩個模組併入組件資訊清單。  
  
 Visual Studio 開發環境不支援建立模組。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="example"></a>範例  
 建立 `in.netmodule` 以編譯 `in.cs`：  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>另請參閱

- [-target (C# 編譯器選項)](./target-compiler-option.md)
- [C# 編譯器選項](./index.md)
