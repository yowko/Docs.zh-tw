---
description: -codepage (C# 編譯器選項)
title: -codepage (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: eda4ce5604beb25ae2d72ac94fbbe7dde9695820
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196802"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (C# 編譯器選項)

如果所需的頁面不是系統目前預設的字碼頁，這個選項可指定編譯期間使用的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>引數  

 `id`  
 編譯過程中所有原始程式碼檔使用的字碼頁的 ID。  
  
## <a name="remarks"></a>備註  

 編譯器會先嘗試將所有原始程式檔解譯為 UTF-8。 如果您的原始程式檔不是以 UTF-8 編碼，也不使用 7 位元的 ASCII 字元，則請使用 **-codepage** 選項指定應該使用的字碼頁。 **-codepage** 會套用到您所編譯的所有原始程式碼檔。  

 如需如何尋找系統所支援之字碼頁的詳細資訊，請參閱 [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo)。  
  
 Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
