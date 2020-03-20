---
title: 安全戰略和工程
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: 970627c5de4964ebd5331c488152022fda55bd74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174559"
---
# <a name="wpf-security-strategy---security-engineering"></a>WPF 安全性策略 – 安全性工程
高可信度電腦運算是一項 Microsoft 開發案，用於確保生產安全的程式碼。 可信計算計畫的一個關鍵要素是 Microsoft 安全開發生命週期 （SDL）。 SDL 是一種工程實踐，它與標準工程流程結合使用，以方便安全代碼的交付。 SDL 由十個階段組成，將最佳實踐與形式化、可測量性和其他結構相結合，包括：  
  
- 安全性設計分析  
  
- 以工具為基礎的品質檢查  
  
- 滲透測試  
  
- 最終安全性檢閱  
  
- 產品發行後安全性管理  
  
## <a name="wpf-specifics"></a>WPF 特性  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]工程團隊同時應用和擴展 SDL，其組合包括以下關鍵方面：  
  
 [威脅建模](#threat_modeling)  
  
 [安全性分析和編輯工具](#tools)  
  
 [測試技術](#techniques)  
  
 [重要程式碼管理](#critical_code)  
  
<a name="threat_modeling"></a>
### <a name="threat-modeling"></a>威脅模型  
 威脅建模是 SDL 的核心元件，用於分析系統以確定潛在的安全性漏洞。 一旦識別出漏洞，威脅模型也可確保適當的安全防護已就位。  
  
 高階的威脅模型牽涉到下列重要步驟，藉由使用雜貨店做為範例：  
  
1. **識別資產**。 雜貨店的資產可能包含員工、保險箱、收銀機和庫存。  
  
2. **列舉進入點**。 雜貨店的進入點可能包含前門和後門、窗戶、卸貨平台和空調設備。  
  
3. **使用進入點調查針對資產的攻擊**。 一次可能的攻擊或許會經由「空調」** 進入點，以雜貨店的「保險箱」** 資產為攻擊目標；空調設備可能被拆下，讓保險箱能從中被拖出來，搬到商店外。  
  
 威脅模型套用到整個 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 並包含下列各項：  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 剖析器會如何讀取檔案，將文字對應到對應的物件模型類別，並建立實際的程式碼。  
  
- 如何建立視窗控制代碼 (hWnd)、傳送訊息，以及用來呈現視窗的內容。  
  
- 資料繫結如何取得資源，並與系統互動。  
  
 在開發過程中，這些威脅模型對於識別安全性設計需求和威脅的安全防護相當重要。  
  
<a name="tools"></a>
### <a name="source-analysis-and-editing-tools"></a>來源分析和編輯工具  
 除了 SDL 的手動安全代碼審查元素外，[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]團隊還使用多種工具進行源分析和相關的編輯，以減少安全性漏洞。 使用廣泛的來源工具，包含下列項目：  
  
- **FXCop**：尋找在 Managed 程式碼中的常見安全性問題，從程式碼存取安全性之使用狀況的繼承規則，到如何安全地相互操作 Unmanaged 程式碼。 請參閱 [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29)。  
  
- **Prefix/Prefast**：找出 Unmanaged 程式碼中的安全性漏洞及常見安全性問題，例如緩衝區滿溢、格式字串問題和錯誤檢查。  
  
- **禁止的應用程式開發介面**：搜尋原始程式碼，來識別已知會造成安全性問題之函式的意外使用，例如 `strcpy`。 一旦確定，這些函數將被更安全的替代項替換。  
  
<a name="techniques"></a>
### <a name="testing-techniques"></a>測試技術  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 使用不同的安全性測試技術，包含：  
  
- **白盒測試**：測試人員查看原始程式碼，然後構建漏洞利用測試。
  
- **黑箱測試**：測試人員藉由檢查應用程式開發介面和功能，試著找出安全性漏洞，然後嘗試攻擊產品。  
  
- **從其他產品減輕安全性問題**：如果相關，則測試來自相關產品的安全性問題。 例如，已確定並嘗試 Internet Explorer 大約 60 個安全問題的適當變體，並嘗試它們[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]適用于 。  
  
- **透過檔案模糊測試進行以工具為基礎的滲透測試**：檔案模糊測試是透過各種輸入來惡意探索檔案讀取器的輸入範圍。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 中使用這項技術的其中一個範例是用來檢查影像解碼程式碼中的錯誤。  
  
<a name="critical_code"></a>
### <a name="critical-code-management"></a>重要程式碼管理  
 對於 XAML 瀏覽器應用程式 （XBAPs），[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]使用 .NET Framework 支援來標記和跟蹤提升特權的安全關鍵代碼來構建安全沙箱（請參閱[WPF 安全性原則](wpf-security-strategy-platform-security.md)**中的安全關鍵方法**- 平臺安全）。 假設在安全性關鍵程式碼上的安全性需求很高，這類程式碼會接收額外層級的來源管理控制和安全性稽核。 大約 5% 到 10%的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 由經過專門的檢閱小組檢閱的安全性關鍵程式碼所組成。 原始程式碼和簽入程序是由追蹤安全性關鍵程式碼來管理，以及對應每個重要的實體 (也就是一個包含關鍵程式碼的方法) 至其登出狀態。 登出狀態包含一或多個檢閱者的名稱。 每個 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 的每日建置會比較該關鍵程式碼和前一個建置的關鍵程式碼，以檢查未經核准的變更。 如果工程師修改未經檢閱小組核准的關鍵程式碼，它會被識別並被立即修正。 此程序能在 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 沙箱程式碼上套用和維護特別高層級的監督。  
  
## <a name="see-also"></a>另請參閱

- [安全性](security-wpf.md)
- [WPF 部分信任安全性](wpf-partial-trust-security.md)
- [WPF 安全性策略 – 平台安全性](wpf-security-strategy-platform-security.md)
- [可信任的電腦運算](https://www.microsoft.com/mscorp/twc/default.mspx)
- [.NET 的安全性](../../standard/security/index.md)
