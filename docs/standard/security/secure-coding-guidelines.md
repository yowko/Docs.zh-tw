---
title: .NET 的安全編碼指南
ms.date: 06/28/2018
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a8f0dfc1a2b5e09722876b73281ed1d8b6334e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018641"
---
# <a name="secure-coding-guidelines"></a>安全編碼指南

辨識項架構的安全性和程式碼存取安全性提供十分強大的明確機制以實作安全性。 大部分的應用程式程式碼可以直接使用由.NET 實作的基礎結構。 某些情況還需要其他的應用程式特定安全性 (藉由擴充安全性系統或是使用新的臨機操作方法來建置)。

使用.NET 強制執行權限和其他強制程式碼中的，您應該可以設置防線來防止惡意程式碼存取，您不想要有的資訊或執行其他不當動作。 此外，在所有使用受信任程式碼的可預期案例中，您必須在安全性與可用性之間達成平衡。

本概觀說明設計程式碼以搭配使用安全性系統時，可以採用的不同方式。

## <a name="securing-resource-access"></a>保護資源存取

當設計和撰寫程式碼時，您需要保護並限制程式碼對資源的存取，特別是當使用或叫用未知來源的程式碼時。 因此，請牢記下列技術，以確保程式碼是安全的︰

- 請勿使用程式碼存取安全性 (CAS)。

- 請勿使用部分信任程式碼。

- 請勿使用[AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute)屬性 (APTCA)。

- 請勿使用 .NET 遠端處理。

- 請勿使用分散式元件物件模型 (DCOM)。

- 請勿使用二進位格式器。

不支援程式碼存取安全性和安全性透明程式碼做為部分信任程式碼與安全性界限。 建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。 替代的安全性措施包括︰

- 虛擬化

- AppContainers

- 作業系統 (OS) 使用者和權限

- Hyper-V 容器

## <a name="security-neutral-code"></a>安全性中性的程式碼

安全性中性的程式碼與安全性系統並無明顯關聯。 它會使用接收到的任何使用權限來執行。 安全性中性的程式碼雖然無法攔截與受保護的作業 （例如使用檔案、 網路等等） 相關聯的安全性例外狀況的應用程式可能會導致未處理的例外狀況，仍會在.NET 中充分利用的安全性技術.

安全性中性程式庫具有您須了解的特殊特性。 假設您的程式庫提供使用檔案或呼叫 unmanaged 程式碼的 API 項目。 如果您的程式碼沒有對應的權限，它將不會執行所述。 然而，即使程式碼擁有使用權限，呼叫它的任何應用程式程式碼也必須要有相同的使用權限才能運作。 如果呼叫程式碼沒有正確的權限，<xref:System.Security.SecurityException>出現程式碼存取安全性堆疊查核行程。

## <a name="application-code-that-isnt-a-reusable-component"></a>不是可重複使用元件的應用程式程式碼

如果您的程式碼是不會由其他程式碼呼叫的應用程式的一部分，安全性很簡單，以及特殊的程式碼可能不需要。 不過請記住，惡意程式碼可以呼叫您的程式碼。 雖然程式碼存取安全性可以制止惡意程式碼存取資源，這類的程式碼還是可以讀取可能含有敏感資訊的欄位或屬性的值。

此外，如果您的程式碼接受網際網路或其他不可靠來源的使用者輸入，您也必須小心惡意輸入。

## <a name="managed-wrapper-to-native-code-implementation"></a>Managed 包裝函式原生程式碼實作

在這個案例中，通常某些有用的功能是在您想提供給 Managed 程式碼的機器碼中所實作。 使用平台叫用或 COM Interop 就可輕鬆撰寫 Managed 包裝函式。 但是，如果您這麼做，包裝函式的呼叫端就必須具有 Unmanaged 程式碼的權限才會成功。 依照預設原則，這表示來自內部網路下載的程式碼，或網際網路不會使用包裝函式。

不會給 unmanaged 程式碼使用這些包裝函式的所有應用程式的權限，最好是讓這些權限給包裝函式程式碼。 如果基礎功能未公開任何資源而且實作也一樣安全，包裝函式就只需要判斷它的權限，讓任何程式碼都可以透過它來呼叫。 當牽涉到資源時，安全性程式碼撰寫應該與下一章節說明的程式庫程式碼的狀況相同。 由於包裝函式對這些資源而言是可能公開的呼叫端，因此小心驗證機器碼安全性的程序是必要的，而且這個程序必須由包裝函式負責執行。

## <a name="library-code-that-exposes-protected-resources"></a>公開 （expose） 的程式庫程式碼受保護的資源

下列的方法是最具威力，因此有潛在危險 （如果誤用） 撰寫程式碼安全性： 您的程式庫做為存取無法否則就如同.NET 類別強制特定資源的其他程式碼的介面使用的資源的權限。 不論您在何處公開資源，您的程式都必須先要求適用於資源的使用權限 (亦即它必須執行安全性檢查)，然後再判斷它的權限，以執行實際的作業。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[設定狀態資料的安全性](securing-state-data.md)|說明如何保護私用成員。|
|[安全性和使用者輸入](security-and-user-input.md)|描述接受使用者輸入之應用程式的安全性疑慮。|
|[安全性和競爭情形](security-and-race-conditions.md)|說明如何避免程式碼中的競爭情形。|
|[安全性和產生作業中的程式碼](security-and-on-the-fly-code-generation.md)|描述產生動態程式碼之應用程式的安全性疑慮。|
|[以角色為基礎的安全性](role-based-security.md)|描述.NET 角色型安全性詳細資料，並提供將它用於您的程式碼中的指示。|
