---
description: '#pragma - C# 參考'
title: '#pragma - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 97d7a786c83a8be21f7fd38873061dba0f9278ae
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137951"
---
# <a name="pragma-c-reference"></a>#pragma (C# 參考)
`#pragma` 將編譯編譯器所在檔案的特殊指示提供給編譯器。 編譯器必須支援指示。 換句話說，您不能使用 `#pragma` 來建立自訂前置處理指示。 Microsoft C# 編譯器支援下列兩個 `#pragma` 指示：  
  
 [#pragma 警告](./preprocessor-pragma-warning.md)  
  
 [#pragma 總和檢查碼](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>語法  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>參數  
 `pragma-name`  
 可辨識的 pragma 名稱。  
  
 `pragma-arguments`  
 Pragma 特定引數。  
  
## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 預處理器指示詞](./index.md)
- [#pragma 警告](./preprocessor-pragma-warning.md)
- [#pragma 總和檢查碼](./preprocessor-pragma-checksum.md)
