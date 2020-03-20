---
title: 從 .NET Framework 1.1 移轉
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: 11fe9ba36d32a4c9fe363b48f76a8bb2b24f073b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974974"
---
# <a name="migrate-from-the-net-framework-11"></a>從 .NET 框架 1.1 遷移

Windows 7 和更高版本的 Windows 作業系統不支援 .NET 框架 1.1。 因此，針對 .NET 框架 1.1 的應用程式在 Windows 7 或更高版本的作業系統版本上未經修改就無法運行。 本主題討論運行針對 Windows 7 和更高版本的 Windows 作業系統的 .NET 框架 1.1 的應用程式所需的步驟。 有關 .NET 框架 1.1 和 Windows 8 的詳細資訊，請參閱[在 Windows 8 和更高版本中運行 .NET 框架 1.1 應用](../install/run-net-framework-1-1-apps.md)。

## <a name="retarget-or-recompile"></a>重新置放或重新編譯

有兩種方法可以使使用 .NET 框架 1.1 編譯的應用程式在 Windows 7 或更高版本的 Windows 作業系統上運行：

- 將應用程式重新置放為在 .NET 框架 4 和更高版本下運行。 重新置放要求您向應用程式的設定檔中添加[\<受支援的 Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md)元素，以允許它在 .NET 框架 4 和更高版本中運行。 這類組態檔的形式如下：

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- 使用以 .NET 框架 4 或更高版本為目標的編譯器重新編譯應用程式。 如果您原本使用 Visual Studio 2003 來開發及編譯解決方案，您可以在 Visual Studio 2010 (更新版本也可以) 中開啟此解決方案，並且使用 [專案相容性]**** 對話方塊來將此解決方案和專案檔從 Visual Studio 2003 使用的格式轉換成 Microsoft Build Engine (MSBuild) 格式。

不論您偏好重新編譯應用程式還是重新設定應用程式的目標，您都必須決定您的應用程式是否會受到較新 .NET Framework 版本中引入的任何變更所影響。 這些變更有兩種：

- 在 .NET Framework 1.1 與較新版 .NET Framework 之間發生的重大變更。

- 在 .NET Framework 1.1 與較新版 .NET Framework 之間，標示為已取代或已過時的型別和型別成員。

無論您是重新設定應用程式的目標還是重新編譯，您都應該針對 .NET Framework 1.1 之後發行的每一個 .NET Framework 版本來檢閱重大變更及過時的型別和成員。

## <a name="breaking-changes"></a>重大變更

當發生重大變更時，重新設定目標及重新編譯的應用程式可能會有替代解決辦法可用 (視特定變更而定)。 在某些情況下，您可以將子項目添加到應用程式的設定檔的[\<運行時>](../configure-apps/file-schema/startup/supportedruntime-element.md)元素以還原以前的行為。 例如，下列組態檔會還原 .NET Framework 1.1 中使用的字串排序和比較行為，而且可以搭配重新設定目標或重新編譯的應用程式使用。

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

但是在某些情況下，您可能必須修改原始程式碼及重新編譯應用程式。

若要評估可能的重大變更對您的應用程式的影響，您必須檢閱以下變更清單：

- [.NET Framework 2.0 中的重大變更](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10))記錄可能會影響以 .NET Framework 1.1 為目標之應用程式的 .NET Framework 2.0 SP1 變更。

- [.NET Framework 3.5 SP1 中的變更](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10))記錄在 .NET Framework 3.5 和 .NET Framework 3.5 SP1 之間的變更。

- [.NET Framework 4 移轉問題](net-framework-4-migration-issues.md)中記載 .NET Framework 3.5 SP1 和 .NET Framework 4 之間的變更。

## <a name="obsolete-types-and-members"></a>過時的類型和成員

對於重新設定目標的應用程式和重新編譯的應用程式而言，已被取代的型別和成員的影響有些不同。 使用過時的型別和成員將不會影響重新設定目標的應用程式，除非已經從其組件中實際移除過時的型別或成員。 重新編譯使用過時型別或成員的應用程式通常會產生編譯器警告，而不是編譯器錯誤。 但是在某些情況下，它會產生編譯器錯誤，而且使用過時型別或成員的程式碼無法成功編譯。 在此情況下，您必須重新撰寫呼叫過時型別或成員的原始程式碼，然後重新編譯應用程式。 如需過時類型和成員的詳細資訊，請參閱[類別庫中的過時功能](../whats-new/whats-obsolete.md)。

若要評估自從 .NET Framework 2.0 SP1 發行之後已被取代之型別和成員的影響，請參閱[類別庫中的過時功能](../whats-new/whats-obsolete.md)。 針對 .NET Framework 2.0 SP1、.NET Framework 3.5 和 .NET Framework 4，檢閱淘汰的型別和成員清單。
