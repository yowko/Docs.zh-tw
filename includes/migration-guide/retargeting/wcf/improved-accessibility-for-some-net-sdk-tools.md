---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614385"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>某些 .NET SDK 工具之改善的協助工具

#### <a name="details"></a>詳細資料

在 .NET Framework SDK 4.7.1 中，SvcConfigEditor.exe 和 SvcTraceViewer.exe 工具已透過修正不同的協助工具問題而得到改善。 其中大部分是小問題，例如未定義名稱，或未正確實作某些 UI 自動化模式。 雖然許多使用者不會察覺到這些不正確的值，但使用螢幕讀取器等輔助技術的客戶會發現這些 SDK 工具更容易存取。 當然，這些修正程式會變更一些先前的行為，例如鍵盤焦點順序。為了取得這些工具的所有協助工具修正程式，您可以將下列程式碼新增至 app.config 檔案：

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |
