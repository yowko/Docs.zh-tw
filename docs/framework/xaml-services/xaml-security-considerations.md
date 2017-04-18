---
title: "XAML Security Considerations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security [XAML Services], .NET XAML services"
  - "XAML security [XAML Services]"
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# XAML Security Considerations
本主題說明在使用 XAML 和 .NET Framework XAML 服務 API 時保有應用程式安全性的最佳作法。  
  
## 應用程式中未受信任的 XAML  
 最簡單的說，未受信任的 XAML 就是您的應用程式未明確加入或發出的任何 XAML 原始碼。  
  
 根據這個定義，已在受信任且已簽署的組件中編譯或儲存為 `resx` 類資源的 XAML，本質上不是未受信任的 XAML。  您對整個組件有多信任，該 XAML 就會受到多信任。  在大部分情況下，您要擔心的只有要對鬆散 XAML 給予多少信任，所謂鬆散 XAML 是指您從資料流或其他 IO 載入的 XAML 原始碼。  鬆散 XAML 不是具有部署和封裝基礎結構之應用程式模型中的特定元件或功能。  不過，組件可能會實作牽涉到載入鬆散 XAML 的行為。  
  
 對於未受信任的 XAML，您通常應將其視同未受信任的程式碼。  請使用沙箱環境或其他環境，防止可能的未受信任 XAML 存取您的受信任程式碼。  
  
 XAML 功能的本質讓 XAML 有權建構物件並設定物件的屬性。  這些功能也包括存取型別轉換子、對應和存取應用程式定義域中的組件、使用標記延伸、`x:Code` 區塊等等。  
  
 除了 XAML 的語言層級功能以外，許多技術也會使用 XAML 來定義 UI。  載入未受信任的 XAML，可能等於載入假冒的惡意 UI。  
  
## 讓讀取器和寫入器共用內容  
 .NET Framework XAML 服務的 XAML 讀取器和 XAML 寫入器架構，通常需要將 XAML 讀取器共用給 XAML 寫入器，不然就是需要共用的 XAML 結構描述內容。  如果您在撰寫 XAML 節點迴圈邏輯或是提供自訂儲存路徑，即可能需要共用物件或內容。  您不應讓受信任和未受信任的程式碼共用 XAML 讀取器執行個體、非預設 XAML 結構描述內容，或是 XAML 讀取器\/寫入器類別的設定。  
  
 在大多數需要針對 CLR 型別備份而撰寫 XAML 物件的情節和作業中，只能使用預設 XAML 結構描述內容。  預設 XAML 結構描述內容不會明確加入可能破壞完全信任的設定。  因此，讓受信任與未受信任的 XAML 讀取器\/寫入器元件共用內容，並無安全上的問題。  但如果您這麼做，最好還是將這些讀取器和寫入器分置在不同的 <xref:System.AppDomain> 範圍，其中一個範圍是設為只獲部分信任的專用沙箱環境。  
  
## XAML 命名空間與組件信任  
 XAML 如何將自訂 XAML 命名空間對應解譯成組件的相關基本未限定語法與定義，無法在受信任與未受信任的組件載入應用程式之中時加以區分。  因此在技術上，未受信任的組件可以假冒受信任組件的預定 XAML 命名空間對應，然後擷取 XAML 原始碼的已宣告物件和屬性資訊。  若要避免這種不安全的情況，您的預定 XAML 命名空間對應應該要以下列其中一項技術來建立：  
  
-   在由您應用程式的 XAML 所建立的任何 XAML 命名空間對應中，使用具有強式名稱的完整限定組件名稱。  
  
-   為您的 XAML 讀取器和 XAML 物件寫入器建構特定的 <xref:System.Xaml.XamlSchemaContext>，以將組件對應限定在固定一組參考組件。  請參閱 <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>。  
  
## XAML 型別對應和型別系統存取  
 XAML 支援自己的型別系統，這在許多方面都對應於 CLR 實作基本 CLR 型別系統的方式。  但是，針對某些型別意識面 \(您要根據型別資訊決定是否信任某個型別\)，您應該聽從 CLR 備份型別中的型別資訊。  這是因為 XAML 型別系統的特定報告功能有些仍保留為虛擬方法，因此不完全在原始 .NET Framework XAML 服務實作的控制下。  因為 XAML 型別系統是可擴充的，所以有這些擴充點存在，以便利用 XAML 本身的擴充性和其可能的替代型別對應策略，而不是使用預設 CLR 備份的實作和預設 XAML 結構描述內容。  如需詳細資訊，請參閱 <xref:System.Xaml.XamlType> 和 <xref:System.Xaml.XamlMember> 數項屬性的特定注意事項。  
  
## 請參閱  
 <xref:System.Xaml.Permissions.XamlAccessLevel>