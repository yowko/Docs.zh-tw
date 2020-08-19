---
title: .NET Framework 中的過時功能
description: 瞭解 .NET 類別庫如何將成員標示為已過時。 瞭解 ObsoleteAttribute 屬性、如何處理過時的類型和成員等等。
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 188d9184476e58fb679421467cd68e2ea8a8a101
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558864"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>.NET Framework 類別庫中已淘汰的功能

.NET 會隨著時間而改變。 每個新版本都會加入一些提供新功能的新類型和類型成員。 現有的類型及其成員也會隨著時間改變。 例如，某些型別在支援的技術被取代為新的技術時變得較不重要，而某些方法則是以某種方式較佳的較新方法取代。

.NET Framework 和 common language runtime 致力於支援回溯相容性 (讓以某個 .NET Framework 版本開發的應用程式在下一版的 .NET Framework) 上執行。 這點會讓您難以單純地移除類型或類型成員。 相反地，.NET 會將類型或類型成員標示為已淘汰或已淘汰，因此不應再使用。 取代類型或成員時需要為其加上標記，以便讓開發人員了解該類型或成員即將消失，而且有時間來回應其移除。 不過，使用該類型或成員的現有程式碼會繼續在新的 .NET 版本中執行。

> [!NOTE]
> 已 *淘汰* 和已 *淘汰的* 條款在套用至 .net 類型和成員時，具有相同的意義。

## <a name="the-obsoleteattribute-attribute"></a>ObsoleteAttribute 屬性

.NET Framework 會使用 <xref:System.ObsoleteAttribute> 屬性來標記某個類型或類型成員，表示該類型或類型成員已過時。 如果將這個屬性套用至某個類型或成員，就表示未來的某個 .NET Framework 版本將移除該類型或成員，但不會破壞使用該成員的已編譯程式碼。

除了表示某個類型或類型成員已過時之外，<xref:System.ObsoleteAttribute> 也會定義編譯器如何處理包含該類型或成員的原始程式碼。 編譯器可能會編譯程式碼但發出警告訊息，也可能會將類型或成員的使用視為錯誤。 在第一種情況下，雖然程式碼可以成功編譯，但是警告訊息會指出類型或成員已過時。 在第二種情況下，編譯會失敗。

即使編譯產生錯誤而非警告訊息，<xref:System.ObsoleteAttribute> 並不會影響執行階段行為。 也就是說，使用該類型或成員而且已成功編譯的應用程式一定會順利執行。 只有嘗試重新編譯使用該類型或成員之應用程式的作業會失敗。

## <a name="how-to-handle-obsolete-types-and-members"></a>如何處理已淘汰的類型和成員

當您升級和重新編譯現有的程式碼時，使用在應用程式中產生編譯器警告的過時類型或成員是完全可接受的作法。 不過，您應該檢閱編譯器警告訊息，以便判斷是否應該變更應用程式程式碼。 如果訊息沒有指向適當的替代方案，您就應該進行下列其中一項步驟：

- 變更程式碼，不使用類型或成員 (如果可能的話)。

     -或-

- 檢閱適用於這個技術領域的文件，以便判斷如何回應取代。

您可以選擇不要針對更新的 .NET Framework 版本重新編譯現有的程式碼， 而改為指定現有已編譯程式碼所執行的目標 .NET Framework 版本。 例如，假設您有一個名為 app1.exe 且已針對 .NET Framework 3.5 編譯的應用程式，但是您想要讓這個應用程式針對 .NET Framework 4.5 執行。 此時，您需要進行下列步驟：

1. 建立主要可執行檔的組態檔，並將它命名為 *appName*.exe.config，其中 *appName* 是應用程式可執行檔的名稱。 針對範例中名為 *app1.exe* 的應用程式，您會建立名為 *app1.exe.config*的設定檔。

2. 將下列內容加入組態檔。

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

若要以特定版本的 .NET Framework 為目標，請將下列其中一個字串值指派給 `version` 屬性：

|.NET Framework 版本|`version` 字串|
|-|-|
|4.8|4.0 版起|
|4.7 (包括 4.7.1 和 4.7.2)|4.0 版起|
|4.6 (包括 4.6.1 和 4.6.2)|4.0 版起|
|4.5 (包括 4.5.1 和 4.5.2)|4.0 版起|
|4|4.0 版起|
|3.5|v2.0.50727|
|2.0|v2.0.50727|
|1.1|v1.1.4322|
|1.0|v1.0.3705|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a>適用于 .NET Framework 4.5 和更新版本的過時 Api

- [過時的類型](obsolete-types.md)
- [過時的成員](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a>舊版的過時 Api

- [.NET Framework 4 中過時的類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))
- [.NET Framework 4 中過時的成員](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))
- [.NET Framework 3.5 的過時清單](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))
- [.NET Framework 2.0 的過時清單](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>請參閱

- [\<supportedRuntime> 元素](../configure-apps/file-schema/startup/supportedruntime-element.md)
