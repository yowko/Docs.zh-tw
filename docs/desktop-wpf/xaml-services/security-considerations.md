---
title: XAML 安全性考量
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 1864910b339c74e3033fb4d6d8baebffada1a4f8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071686"
---
# <a name="xaml-security-considerations"></a>XAML 安全注意事項

本文介紹了在使用 XAML 和 .NET XAML 服務 API 時應用程式中安全性的最佳做法。

## <a name="untrusted-xaml-in-applications"></a>應用程式中的不受信任的 XAML

在最一般意義上,不受信任的 XAML 是應用程式未具體包含或發出的任何 XAML 源。

編譯到受信任和簽名程式集中的`resx`-類型資源或存儲為 -類型的 XAML 本質上不受信任。 您可以像信任整個程式集一樣信任 XAML。 在大多數情況下,您只關心鬆散的 XAML 的信任方面,這是從流或其他 I/O 載入的 XAML 源。 鬆散 XAML 不是具有部署和打包基礎結構的應用程式模型的特定元件或功能。 但是,程式集可能實現涉及載入鬆散 XAML 的行為。

對於不受信任的 XAML,通常應該將其視為不受信任的代碼。 使用沙箱或其他隱喻來防止可能不受信任的 XAML 訪問受信任的代碼。

XAML 功能的性質使 XAML 有權構造物件並設置其屬性。 這些功能還包括存取類型轉換器、映射和存取應用程式域中的程式集,使用標記`x:Code`擴展、塊等。

除了語言級功能外,XAML 還用於許多技術的 UI 定義。 載入不受信任的 XAML 可能意味著載入惡意欺騙 UI。

## <a name="sharing-context-between-readers-and-writers"></a>讀者與作者之間分享上下文

.NET XAML 服務架構結構適用於 XAML 讀取器和 XAML 編寫器,通常需要將 XAML 讀取器共用給 XAML 編寫器或共用 XAML 架構上下文。 如果要編寫 XAML 節點迴圈邏輯或提供自訂保存路徑,則可能需要共用物件或上下文。 不要在受信任的代碼和不受信任的代碼之間共用 XAML 讀取器實例、非預設 XAML 架構上下文或 XAML 讀取器/寫入器類的設置。

大多數涉及基於 CLR 的類型備份的 XAML 物件寫入的方案和操作都只能使用預設的 XAML 架構上下文。 預設 XAML 架構上下文沒有明確包含可能危及完全信任的設置。 因此,在受信任的和不受信任的 XAML 讀取器/寫入器元件之間共用上下文是安全的。 但是,如果您這樣做,最好還是將這些讀者和作者保存在單獨的<xref:System.AppDomain>作用域中,其中一個專門打算/沙箱用於部分信任。

## <a name="xaml-namespaces-and-assembly-trust"></a>XAML 命名空間與程式集信任

XAML 如何將自定義 XAML 命名空間映射解釋為程式集的基本限定語法和定義不會區分載入到應用程式域中的受信任程式集和不受信任的程式集。 因此,從技術上講,不受信任的程式集可以欺騙受信任的程式集的預期 XAML 命名空間映射並捕獲 XAML 源聲明的物件和屬性資訊。 如果您有安全要求以避免這種情況,則應使用以下技術之一進行預期的 XAML 命名空間映射:

- 在應用程式的 XAML 進行的任何 XAML 命名空間映射中使用具有強名稱的完全限定程式集名稱。

- 通過建構特定於 XAML 讀取器和<xref:System.Xaml.XamlSchemaContext>XAML 物件編寫器的程式集映射,將程式集映射限制為一組固定的引用程式集。 請參閱＜<xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>＞。

## <a name="xaml-type-mapping-and-type-system-access"></a>XAML 類型映射與類型系統存取

XAML 支援其自己的類型系統,在許多方面,該系統是CLR如何實現基本CLR類型系統的對等體。 但是,對於類型感知的某些方面,如果您根據類型資訊對類型做出信任決策,則應服從 CLR 支援類型中的類型資訊。 這是因為 XAML 類型系統的一些特定報告功能作為虛擬方法處於打開狀態,因此並不完全受原始 .NET XAML 服務實現的控制。 存在這些擴展點是因為 XAML 類型系統是可擴展的,以匹配 XAML 本身的可擴充性及其可能的替代類型對應策略與預設 CLR 支援的實現和預設 XAML 架構上下文。 有關詳細資訊,請參閱<xref:System.Xaml.XamlType>有關<xref:System.Xaml.XamlMember>和的幾種屬性的特定註釋。

## <a name="see-also"></a>另請參閱

- <xref:System.Xaml.Permissions.XamlAccessLevel>
