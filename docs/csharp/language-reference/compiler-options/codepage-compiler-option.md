---
title: "-codepage (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e17622256ca6a0344797ba16e007ba6feb8f873
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="codepage-c-compiler-options"></a>/codepage (C# 編譯器選項)
如果所需的頁面不是系統目前預設的字碼頁，這個選項可指定編譯期間使用的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a>引數  
 `id`  
 編譯過程中所有原始程式碼檔使用的字碼頁的 ID。  
  
## <a name="remarks"></a>備註  
 如果您編譯一或多個不是使用電腦的預設字碼頁建立的原始程式碼檔，則可以使用 **/codepage** 選項指定應該使用的字碼頁。 **/codepage** 會套用到您所編譯的所有原始程式碼檔。  
  
 如果原始程式檔是使用您電腦中正在作用中的同一個字碼頁所建立的，或者原始程式檔是使用 UNICODE 或 UTF-8 所建立的，則不需要使用 **/codepage**。  
  
 如需如何尋找系統所支援之字碼頁的詳細資訊，請參閱 [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx)。  
  
 Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
