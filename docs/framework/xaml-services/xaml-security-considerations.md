---
title: XAML 安全性考量
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: ef47e7e370082a2050406710edcb62d0967df8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562358"
---
# <a name="xaml-security-considerations"></a>XAML 安全性考量
本主題描述在應用程式中的安全性最佳作法，當您使用 XAML 和.NET Framework XAML 服務 API。  
  
## <a name="untrusted-xaml-in-applications"></a>在應用程式中不受信任的 XAML  
 最常見的意義而言，不受信任的 XAML 是未特別包含您的應用程式或發出任何 XAML 來源。  
  
 編譯成或儲存為 XAML `resx`-類型受信任和簽署組件內的資源不是原本就是不受信任。 如往常般信任整個組件中，您可以信任的 XAML。 在大部分情況下，您才關心鬆散的 XAML，這是您從資料流或其他 I/O 載入 XAML 來源的信任層面。 鬆散的 XAML 不是特定元件或功能的應用程式模型的部署與封裝基礎結構。 不過，組件可能會實作牽涉到載入鬆散 XAML 的行為。  
  
 針對不受信任的 XAML，您應該將它視為通常相同它已不受信任的程式碼。 若要防止存取您信任的程式碼可能不受信任的 XAML 使用沙箱或其他象徵物。  
  
 性質的 XAML 功能可讓 XAML 建構物件，並設定其屬性的權限。 這些功能也包括存取型別轉換子，對應及存取組件在應用程式網域中，使用標記延伸`x:Code`區塊，依此類推。  
  
 除了其語言層級功能，XAML 用於 UI 定義許多技術中。 載入未受信任的 XAML，可能表示載入惡意的詐騙 UI。  
  
## <a name="sharing-context-between-readers-and-writers"></a>共用讀取器與寫入器之間的內容  
 .NET Framework XAML 服務 XAML 讀取器和 XAML 寫入器架構通常需要在共用的 XAML 寫入器，或共用的 XAML 結構描述內容的 XAML 讀取器。 共用的物件或內容可能需要當您要撰寫 XAML 節點迴圈邏輯，或提供自訂的儲存路徑。 您不應共用的 XAML 讀取器執行個體、 非預設 XAML 結構描述內容或設定受信任和未受信任的程式碼之間的 XAML 讀取器/寫入器類別。  
  
 大部分的案例和牽涉到 XAML 物件寫入為以 CLR 為基礎的類型，支援的作業只可以使用的預設 XAML 結構描述內容。 預設 XAML 結構描述內容未明確包括可能會危及完全信任的設定。 因此，它可以安全地共用信任與不受信任的 XAML 讀取器/寫入器元件之間的內容。 不過，如果您這麼做時，它仍然是最佳做法是在不同保留這類的讀取器和寫入器<xref:System.AppDomain>範圍，其中特別預期/沙箱化部分信任。  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>XAML 命名空間和組件信任  
 基本不合格的語法和 XAML 如何解譯的組件的自訂 XAML 命名空間對應的定義不會區分受信任和未受信任組件載入至應用程式定義域。 因此，它技術上可能會偽造受信任組件的預期的 XAML 命名空間對應，並擷取宣告 XAML 來源的物件和屬性資訊的不受信任組件。 如果您有安全性需求，以避免這種情況，您預期的 XAML 命名空間對應應該可以使用下列技巧：  
  
-   使用應用程式的 XAML 所做的任何 XAML 命名空間對應中的強式名稱的完整組件名稱。  
  
-   限制對應至一組固定的參考組件，建構特定的組件<xref:System.Xaml.XamlSchemaContext>XAML 讀取器和 XAML 物件寫入器。 請參閱 <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>。  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>XAML 型別對應和類型系統存取  
 XAML 支援它自己的型別系統，其中有許多方式等 CLR 實作基本的 CLR 型別系統的方式。 不過，您會在此進行信任決策是根據其類型資訊的類型的類型感知的特定部分，您應該遵循在支援類型的 CLR 型別資訊。 這是因為某些特定 XAML 類型系統的報告功能會保持在開啟做為虛擬方法，因此，不完全控制原始的.NET Framework XAML 服務實作。 這些擴充點存在，因為 XAML 類型系統可延伸，以符合 XAML 本身的擴充性和其可能的替代類型對應策略和預設 CLR 為基礎的實作及預設 XAML 結構描述內容。 如需詳細資訊，請參閱特定的備忘稿幾個屬性的<xref:System.Xaml.XamlType>和<xref:System.Xaml.XamlMember>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xaml.Permissions.XamlAccessLevel>
