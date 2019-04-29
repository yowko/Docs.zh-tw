---
title: 封送處理 MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463c8e42e76a61eb0820c1af72c20d004161ad25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753968"
---
# <a name="marshaling-mda"></a>封送處理 MDA
當 CLR 設定方法參數或結構之欄位的封送處理資訊時，會啟動 `marshaling` managed 偵錯助理 (MDA)。 此 MDA 不適用於 JIT 編譯的組件。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>Output  
 MDA 會顯示在 managed 和 unmanaged 內容的參數或欄位類型，以及包含類型的結構或方法。  以下是欄位輸出的範例：  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>組態  
 MDA 組態可讓您根據相關的欄位或方法名稱篩選報告的封送處理資訊。  下列範例顯示如何使用 `methodFilter``fieldFilter` 和 `match` 項目以指定篩選條件。  將 `name` 屬性設定為星號 (*) 會比對所有項目。  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
