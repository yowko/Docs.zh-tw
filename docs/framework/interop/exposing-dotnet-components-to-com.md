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
ms.openlocfilehash: 1879f5b5aa2fbe6b0e51f9b38fca3af1f4c0cedf
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971762"
---
# <a name="exposing-net-framework-components-to-com"></a>將 .NET Framework 元件公開給 COM

撰寫 .NET 類型和從 Unmanaged 程式碼取用該類型，對開發人員來說是不同的活動。 本節描述幾個撰寫與 COM 用戶端交互操作之 Managed 程式碼的祕訣：

- [限定交互操作的 .NET 類型](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md)。

     所有您想要公開給 COM 的 Managed 類型、方法、屬性、欄位和事件，都必須是公用的。 型別必須有公用無參數建構函式，它是可透過 COM 叫用的唯一建構函式。

- [套用 Interop 屬性](../../../docs/standard/native-interop/apply-interop-attributes.md)。

     Managed 程式碼中的自訂屬性，可以加強元件的互通性。

- [封裝 COM 的組件](../../../docs/framework/interop/packaging-an-assembly-for-com.md)。

     COM 開發人員可能會要求您彙總參考及部署組件的相關步驟。

 此外，本節還會找出與從 COM 用戶端取用 Managed 類型的相關工作。

## <a name="to-consume-a-managed-type-from-com"></a>從 COM 取用 Managed 類型

1. [向 COM 登錄組件](../../../docs/framework/interop/registering-assemblies-with-com.md)。

     組件 (與型別程式庫) 中的類型必須在設計階段登錄。 如果安裝程式不登錄組件，請指示 COM 開發人員使用 Regasm.exe。

2. [參考 COM 的 .NET 類型](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)。

     COM 開發人員可以使用目前所用的相同工具和技術，參考組件中的類型。

3. [呼叫 .NET 物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))。

     COM 開發人員可以用在任何 Unmanaged 類型上呼叫方法的相同方式，在 .NET 物件上呼叫方法。 例如，COM **CoCreateInstance** API 會啟動 .NET 物件。

4. [部署供 COM 存取的應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))。

     強式名稱組件可以安裝在全域組件快取，而且需要其發行者的簽章。 沒有強式名稱的組件必須安裝在用戶端的應用程式目錄中。

## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](../../../docs/framework/interop/index.md)
- [COM Interop 範例：COM 用戶端與 .NET 伺服器](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
