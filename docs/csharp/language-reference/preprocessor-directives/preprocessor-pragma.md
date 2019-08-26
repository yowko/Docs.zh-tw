---
title: '#pragma - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605664"
---
# <a name="pragma-c-reference"></a>#pragma (C# 參考)
`#pragma` 將編譯編譯器所在檔案的特殊指示提供給編譯器。 編譯器必須支援指示。 換句話說，您不能使用 `#pragma` 來建立自訂前置處理指示。 Microsoft C# 編譯器支援下列兩個 `#pragma` 指示：  
  
 [#pragma warning](./preprocessor-pragma-warning.md)  
  
 [#pragma checksum](./preprocessor-pragma-checksum.md)  
  
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

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 前置處理器指示詞](./index.md)
- [#pragma warning](./preprocessor-pragma-warning.md)
- [#pragma checksum](./preprocessor-pragma-checksum.md)
