---
title: 安全程式碼撰寫方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET Framework], security
- code security, options
- security-neutral code
- security [.NET Framework], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8d61e76a657c7341ec7dfcede6d7dc9943d4659
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="secure-coding-guidelines"></a>安全程式碼撰寫方針
辨識項架構的安全性和程式碼存取安全性提供十分強大的明確機制以實作安全性。 大部分的應用程式程式碼都只需要使用 .NET Framework 所實作的基礎結構即可。 某些情況還需要其他的應用程式特定安全性 (藉由擴充安全性系統或是使用新的臨機操作方法來建置)。  
  
 透過在您的程式碼中使用 .NET Framework 強制使用權限和其他強制方法，您應該可以設置防線，防止惡意程式碼取得您不想讓它取得的資訊，或是執行其他不當動作。 此外，在所有使用受信任程式碼的可預期案例中，您必須在安全性與可用性之間達成平衡。  
  
 本概觀說明設計程式碼以搭配使用安全性系統時，可以採用的不同方式。  
  
## <a name="securing-resource-access"></a>保護資源存取  
 當設計和撰寫程式碼時，您需要保護並限制程式碼對資源的存取，特別是當使用或叫用未知來源的程式碼時。 因此，請牢記下列技術，以確保程式碼是安全的︰  
  
-   請勿使用程式碼存取安全性 (CAS)。  
  
-   請勿使用部分信任程式碼。  
  
-   請勿使用 .NET 遠端處理。  
  
-   請勿使用分散式元件物件模型 (DCOM)。  
  
-   請勿使用二進位格式器。  
  
 程式碼存取安全性與安全性透明的程式碼，將不會如同部分程式碼受信任的安全性界限般受到支援。 建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。 替代的安全性措施包括︰  
  
-   虛擬化  
  
-   AppContainers  
  
-   作業系統 (OS) 使用者和權限  
  
-   Hyper-V 容器  
  
## <a name="security-neutral-code"></a>安全性中性的程式碼  
 安全性中性的程式碼與安全性系統並無明顯關聯。 它會使用接收到的任何使用權限來執行。 雖然當應用程式無法攔截與受保護作業 (例如使用檔案、網路等) 關聯的安全性例外狀況時，可能會導致無法處理的例外狀況，安全性中性的程式碼仍然可以利用 .NET Framework 安全性技術。  
  
 安全性中性程式庫具有您須了解的特殊特性。 假設您的程式庫提供使用檔案或呼叫 Unmanaged 程式碼的 API 項目；如說明所述，如果您的程式碼沒有對應的使用權限，它就不會執行。 然而，即使程式碼擁有使用權限，呼叫它的任何應用程式程式碼也必須要有相同的使用權限才能運作。 如果呼叫程式碼沒有正確的使用權限<xref:System.Security.SecurityException>出現程式碼存取安全性堆疊查核行程。  
  
## <a name="application-code-that-is-not-a-reusable-component"></a>不是重複使用元件的應用程式程式碼  
 如果您的程式碼所屬的應用程式不會被其他程式碼呼叫，安全性的維護便十分簡單，而且可能不需要撰寫特殊的程式碼。 不過請記住，惡意程式碼可以呼叫您的程式碼。 雖然程式碼存取安全性可以制止惡意程式碼存取資源，這類的程式碼還是可以讀取可能含有敏感資訊的欄位或屬性的值。  
  
 此外，如果您的程式碼接受網際網路或其他不可靠來源的使用者輸入，您也必須小心惡意輸入。  
  
## <a name="managed-wrapper-to-native-code-implementation"></a>機器碼實作的 Managed 包裝函式  
 在這個案例中，通常某些有用的功能是在您想提供給 Managed 程式碼的機器碼中所實作。 使用平台叫用或 COM Interop 就可輕鬆撰寫 Managed 包裝函式。 但是，如果您這麼做，包裝函式的呼叫端就必須具有 Unmanaged 程式碼的權限才會成功。 在預設原則中，這表示從內部網路或網際網路下載的程式碼將無法使用包裝函式。  
  
 比較好的作法是將 Unmanaged 程式碼權限授與包裝函式程式碼，而不是將這些權限授與使用這些包裝函式的所有應用程式。 如果基礎功能未公開任何資源而且實作也一樣安全，包裝函式就只需要判斷它的權限，讓任何程式碼都可以透過它來呼叫。 當牽涉到資源時，安全性程式碼撰寫應該與下一章節說明的程式庫程式碼的狀況相同。 由於包裝函式對這些資源而言是可能公開的呼叫端，因此小心驗證機器碼安全性的程序是必要的，而且這個程序必須由包裝函式負責執行。  
  
## <a name="library-code-that-exposes-protected-resources"></a>公開受保護資源的程式庫程式碼  
 這是安全性程式碼撰寫最具威力的方法，因此也具有潛在的危險 (如果誤用的話)：將您的程式庫當做其他程式碼存取某些特定資源的介面 (如果使用其他方法就無法使用這些資源)，就如同 .NET Framework 的類別對它們使用的資源強制使用權限一般。 不論您在何處公開資源，您的程式都必須先要求適用於資源的使用權限 (亦即它必須執行安全性檢查)，然後再判斷它的權限，以執行實際的作業。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[設定狀態資料的安全性](../../../docs/standard/security/securing-state-data.md)|說明如何保護私用成員。|  
|[安全性和使用者輸入](../../../docs/standard/security/security-and-user-input.md)|描述接受使用者輸入之應用程式的安全性疑慮。|  
|[安全性和競爭情形](../../../docs/standard/security/security-and-race-conditions.md)|說明如何避免程式碼中的競爭情形。|  
|[安全性和產生作業中的程式碼](../../../docs/standard/security/security-and-on-the-fly-code-generation.md)|描述產生動態程式碼之應用程式的安全性疑慮。|  
|[以角色為基礎的安全性](../../../docs/standard/security/role-based-security.md)|詳細描述 .NET Framework 以角色為基礎的安全性，並提供將它用於您的程式碼中的指示。|
