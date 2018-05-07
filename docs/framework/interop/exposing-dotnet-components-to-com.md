---
title: 將 .NET Framework 元件公開給 COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f11928388dba9b0e9b442578bfb7b6f751c2e172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exposing-net-framework-components-to-com"></a>將 .NET Framework 元件公開給 COM
撰寫 .NET 類型和從 Unmanaged 程式碼取用該類型，對開發人員來說是不同的活動。 本節描述幾個撰寫與 COM 用戶端交互操作之 Managed 程式碼的祕訣：  
  
-   [限定交互操作的 .NET 類型](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)。  
  
     所有您想要公開給 COM 的 Managed 類型、方法、屬性、欄位和事件，都必須是公用的。 類型必須有公用的預設建構函式，它是唯一可透過 COM 叫用的建構函式。  
  
-   [套用 Interop 屬性](../../../docs/framework/interop/applying-interop-attributes.md)。  
  
     Managed 程式碼中的自訂屬性，可以加強元件的互通性。  
  
-   [封裝 COM 的組件](../../../docs/framework/interop/packaging-an-assembly-for-com.md)。  
  
     COM 開發人員可能會要求您彙總參考及部署組件的相關步驟。  
  
 此外，本節還會找出與從 COM 用戶端取用 Managed 類型的相關工作。  
  
#### <a name="to-consume-a-managed-type-from-com"></a>從 COM 取用 Managed 類型  
  
1.  [向 COM 登錄組件](../../../docs/framework/interop/registering-assemblies-with-com.md)。  
  
     組件 (與型別程式庫) 中的類型必須在設計階段登錄。 如果安裝程式不登錄組件，請指示 COM 開發人員使用 Regasm.exe。  
  
2.  [參考 COM 的 .NET 類型](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)。  
  
     COM 開發人員可以使用目前所用的相同工具和技術，參考組件中的類型。  
  
3.  [呼叫 .NET 物件](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))。  
  
     COM 開發人員可以用在任何 Unmanaged 類型上呼叫方法的相同方式，在 .NET 物件上呼叫方法。 例如，COM **CoCreateInstance** API 會啟動 .NET 物件。  
  
4.  [部署供 COM 存取的應用程式](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))。  
  
     強式名稱組件可以安裝在全域組件快取，而且需要其發行者的簽章。 沒有強式名稱的組件必須安裝在用戶端的應用程式目錄中。  
  
## <a name="see-also"></a>另請參閱  
 [與 Unmanaged 程式碼互通](../../../docs/framework/interop/index.md)  
 [COM Interop 範例：COM 用戶端與 .NET 伺服器](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
