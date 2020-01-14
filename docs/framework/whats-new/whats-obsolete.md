---
title: .NET Framework 中的過時功能
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: eda60ce9e1396805541229c9756b13cdd167dc72
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901340"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>.NET Framework 類別庫中已淘汰的功能

.NET 會隨著時間變更。 每個新版本都會加入一些提供新功能的新類型和類型成員。 現有的類型及其成員也會隨著時間改變。 例如，某些類型變得較不重要，因為它們所支援的技術是由新的技術所取代，而某些方法則是以某種方式較佳的新方法取代。

.NET Framework 和通用語言執行平臺致力於支援回溯相容性（允許以一個 .NET Framework 版本開發的應用程式在下一版的 .NET Framework 上執行）。 這點會讓您難以單純地移除類型或類型成員。 相反地，.NET 表示類型或類型成員不應再使用，因為它會將它標示為過時或已被取代。 取代類型或成員時需要為其加上標記，以便讓開發人員了解該類型或成員即將消失，而且有時間來回應其移除。 不過，使用類型或成員的現有程式碼會繼續在新版 .NET 中執行。

> [!NOTE]
> 套用至 .NET 類型和成員時，已*過時*和已被*取代*的字詞具有相同的意義。

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

1. 建立主要可執行檔的組態檔，並將它命名為 *appName*.exe.config，其中 *appName* 是應用程式可執行檔的名稱。 在我們的範例中，針對名為*app1*的應用程式，您會建立名為*app1*的設定檔。

2. 將下列內容加入組態檔。

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

若要以 .NET Framework 的特定版本為目標，請將下列其中一個字串值指派給 `version` 屬性：

|.NET Framework 版本|`version` 字串|
|-|-|
|4.8|v4.0|
|4.7 (包括 4.7.1 和 4.7.2)|v4.0|
|4.6 (包括 4.6.1 和 4.6.2)|v4.0|
|4.5 (包括 4.5.1 和 4.5.2)|v4.0|
|4|v4.0|
|3.5|v2.0.50727|
|2.0|v2.0.50727|
|1.1|v1.1.4322|
|1.0|v1.0.3705|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a>.NET Framework 4.5 和更新版本的過時 Api

- [過時的類型](obsolete-types.md)
- [過時的成員](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a>舊版的過時 Api

- [.NET Framework 4 中的過時類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))
- [.NET Framework 4 中過時的成員](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))
- [.NET Framework 3.5 的過時清單](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))
- [.NET Framework 2.0 的過時清單](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>請參閱

- [\<supportedRuntime> 項目](../configure-apps/file-schema/startup/supportedruntime-element.md)
