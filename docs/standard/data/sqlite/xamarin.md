---
title: Xamarin 限制
ms.date: 12/13/2019
description: 說明您在使用 Xamarin 時會遇到的一些限制。
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447164"
---
# <a name="xamarin-limitations"></a>Xamarin 限制

.NET Standard 2.0 的 Sqlite 目標，而且 Xamarin 支援。 下表顯示預設 SQLitePCLRaw 組合提供原生 SQLite 二進位檔的平臺。 如需使用不同配套的詳細資訊，或提供您自己的原生 SQLite 二進位檔，請參閱[自訂 SQLite 版本](custom-versions.md)。

| 平台 | SQLite 二進位檔 |
| --- | --- |
| **Xamarin.Android** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | ✔ |
| **Xamarin.iOS** | ✔ |
| **Xamarin. Mac** | ✔ |
| **TVOS** | ✔ |
| **UWP** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |

## <a name="ios"></a>iOS

Sqlite 會嘗試自動初始化 SQLitePCLRaw 組合。 可惜的是，因為 Xamarin 的預先（AOT）編譯有限制，所以嘗試會失敗，而且您會收到下列錯誤。

> 您必須呼叫`SQLitePCL.raw.SetProvider()`。 如果您使用配套套件，請呼叫`SQLitePCL.Batteries.Init()`來完成此作業。

若要初始化配套，請將下列程式程式碼新增至您的應用程式，然後再使用 Microsoft. Data Sqlite。

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a>另請參閱

* [非同步限制](async.md)
* [自訂 SQLite 版本](custom-versions.md)
