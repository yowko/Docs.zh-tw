---
title: "風險降低︰以指標為基礎的觸控及手寫筆支援 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
caps.latest.revision: 2
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: f93c914e0c1d285cc0f6117e5ae7a0f6338bc549
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>風險降低︰以指標為基礎的觸控及手寫筆支援

以 .NET Framework 4.7 為目標並在從 Windows 10 Creators Update 開始的 Windows 系統上執行的 WPF 應用程式，可啟用選擇性的 `WM_POINTER` 式 WPF 觸控/手寫筆堆疊。

## <a name="impact"></a>影響

開發人員若未明確地啟用以指標為基礎的觸控/手寫筆支援，應該不會看到任何 WPF 觸控/手寫筆行為的變更。

以下是選擇性的 `WM_POINTER` 式觸控/手寫筆堆疊目前已知的問題︰

- 不支援即時筆跡。

   雖然筆跡和手寫筆外掛程式還能運作，但它們是在 UI 執行緒上處理，可能會導致效能不佳。

- 從觸控/手寫筆事件提升為滑鼠事件的變更，因而產生行為變更。

  - 操作可能有不同的行為。

  - 拖放動作無法對觸控輸入顯示適當的回應。 (這不影響手寫筆輸入。)

  - 無法再針對觸控/手寫筆事件起始拖放動作。

      這可能會使應用程式停止回應到偵測到滑鼠輸入為止。 開發人員應改為從滑鼠事件起始拖放動作。

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a>選擇加入 WM_POINTER 式觸控/手寫筆支援

想要啟用此堆疊的開發人員可以將以下內容加入至他們應用程式的 app.config 檔案︰

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

移除此項目或將其值設為 `false` 可關閉這個選擇性的堆疊。

## <a name="see-also"></a>請參閱

[.NET Framework 4.7 中的重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

