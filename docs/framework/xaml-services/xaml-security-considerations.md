---
title: XAML 安全性考量
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 124310497cc2a8e8a816ba90b2c68a16ed342ae6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162668"
---
# <a name="xaml-security-considerations"></a>XAML 安全性考量
本主題描述在應用程式中的安全性最佳作法，當您使用 XAML 和.NET Framework XAML 服務 API。  
  
## <a name="untrusted-xaml-in-applications"></a>在應用程式中不受信任的 XAML  
 最常見的方面來說，不受信任的 XAML 是您的應用程式沒有不是明確地包含或發出任何 XAML 來源。  
  
 編譯成或儲存為 XAML `resx`-信任和已簽署的組件中的型別資源不是原本就是不受信任。 如同您信任整個組件，您可以信任的 XAML。 在大部分情況下，您才關心鬆散的 XAML，這是您從資料流或其他 I/O 載入 XAML 來源的信任層面。 鬆散的 XAML 不是特定元件或功能的部署與封裝基礎結構的應用程式模型。 不過，組件可能會實作包含載入鬆散 XAML 的行為。  
  
 針對未受信任的 XAML，您應該將它視為通常相同它已不受信任的程式碼。 若要防止存取您信任的程式碼可能不受信任的 XAML 使用沙箱或其他的隱喻。  
  
 XAML 功能的本質可讓 XAML 來建構物件，並設定其屬性。 這些功能也包含存取型別轉換子，對應和存取組件在應用程式網域中，使用標記延伸`x:Code`區塊，依此類推。  
  
 除了其語言層級功能，XAML 用來在許多技術中的 UI 定義。 正在載入未受信任的 XAML，可能表示載入惡意的詐騙 UI。  
  
## <a name="sharing-context-between-readers-and-writers"></a>共用讀取器和寫入器之間的內容  
 XAML 讀取器和 XAML 寫入器的.NET Framework XAML 服務架構通常會需要共用是在 XAML 讀取器的 XAML 寫入器，或共用的 XAML 結構描述內容。 共用的物件或內容可能是必要，如果您正在撰寫 XAML 節點迴圈邏輯，或提供自訂儲存路徑。 您不應共用 XAML 讀取器執行個體、 非預設 XAML 結構描述內容或設定受信任和未受信任的程式碼之間的 XAML 讀取器/寫入器類別。  
  
 大部分的案例和涉及 XAML 物件寫入為以 CLR 為基礎的類型，支援的作業可以只使用預設 XAML 結構描述內容。 預設 XAML 結構描述內容未明確包括可能會危害完全信任的設定。 因此，它是安全地共用信任與不受信任的 XAML 讀取器/寫入器元件之間的內容。 不過，如果您這麼做時，仍建議您保留在不同的這類的讀取器和寫入<xref:System.AppDomain>範圍，具有特別想要/沙箱化部分信任的其中一個。  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>XAML 命名空間和組件的信任  
 基本不合格的語法與定義 XAML 如何解譯自訂的 XAML 命名空間對應至組件就不會區分之間受信任和未受信任的組件，以載入應用程式定義域中。 因此，就技術上來說可能不受信任的組件來證明其信任的組件的預定的 XAML 命名空間對應，並擷取 XAML 來源的宣告的物件和屬性資訊。 如果您有安全性需求，以避免這種情況下，您想要的 XAML 命名空間對應應在使用其中一種下列技術：  
  
-   使用您的應用程式的 XAML 所做的任何 XAML 命名空間對應中的強式名稱的完整組件名稱。  
  
-   限制對應至一組固定的參考組件，藉由建構特定的組件<xref:System.Xaml.XamlSchemaContext>您 XAML 讀取器和 XAML 物件寫入器。 請參閱 <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>。  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>XAML 型別對應和型別系統的存取權  
 XAML 支援它自己的型別系統，這在許多方面是 CLR 如何實作基本的 CLR 型別系統之對等。 不過，您會在其中進行信任決策，根據其類型資訊的型別相關的類型感知的特定部分，您應該延後至支援型別在 CLR 中的類型資訊。 這是因為一些 XAML 類型系統的特定報告功能會保持在開啟為虛擬方法，因此，並不是完全在原始的.NET Framework XAML 服務實作的控制之下。 這些擴充點存在，因為 XAML 型別系統可延伸，以符合 XAML 本身的擴充性和其可能的替代類型對應策略與預設 XAML 結構描述內容與預設 CLR 為基礎的實作。 詳細資訊，請參閱特定的附註，數個屬性上<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xaml.Permissions.XamlAccessLevel>
