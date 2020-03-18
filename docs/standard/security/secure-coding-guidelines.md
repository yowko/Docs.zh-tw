---
title: 保護 .NET 的編碼準則
description: 設計要使用的代碼。NET 強制許可權和其他強制，以説明防止惡意程式碼訪問資料或執行其他操作。
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
ms.openlocfilehash: 05f7e039ecdc0cd33baa015872924fb9e1f078aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187720"
---
# <a name="secure-coding-guidelines"></a>安全編碼指南

辨識項架構的安全性和程式碼存取安全性提供十分強大的明確機制以實作安全性。 大多數應用程式代碼只能使用 .NET 實現的基礎結構。 某些情況還需要其他的應用程式特定安全性 (藉由擴充安全性系統或是使用新的臨機操作方法來建置)。

在代碼中使用 .NET 強制許可權和其他強制，應設置障礙，以防止惡意程式碼訪問不希望其擁有的資訊或執行其他不可取的操作。 此外，在所有使用受信任程式碼的可預期案例中，您必須在安全性與可用性之間達成平衡。

本概觀說明設計程式碼以搭配使用安全性系統時，可以採用的不同方式。

## <a name="securing-resource-access"></a>保護資源訪問

當設計和撰寫程式碼時，您需要保護並限制程式碼對資源的存取，特別是當使用或叫用未知來源的程式碼時。 因此，請牢記下列技術，以確保程式碼是安全的︰

- 請勿使用程式碼存取安全性 (CAS)。

- 請勿使用部分信任程式碼。

- 不要使用["允許部分受信任的調用方"](xref:System.Security.AllowPartiallyTrustedCallersAttribute)屬性 （APTCA）。

- 請勿使用 .NET 遠端處理。

- 請勿使用分散式元件物件模型 (DCOM)。

- 請勿使用二進位格式器。

代碼訪問安全和安全透明代碼不支援作為具有部分受信任代碼的安全邊界。 建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。 替代的安全性措施包括︰

- 虛擬化

- AppContainers

- 作業系統 (OS) 使用者和權限

- Hyper-V 容器

## <a name="security-neutral-code"></a>安全中立代碼

安全性中性的程式碼與安全性系統並無明顯關聯。 它會使用接收到的任何使用權限來執行。 儘管無法捕獲與受保護操作（如使用檔、網路等）關聯的安全異常的應用程式可能會導致未處理的異常，但安全中立代碼仍利用 .NET 中的安全技術.

安全性中性程式庫具有您須了解的特殊特性。 假設您的庫提供使用檔或調用非託管代碼的 API 元素。 如果代碼沒有相應的許可權，則代碼不會按照所述運行。 然而，即使程式碼擁有使用權限，呼叫它的任何應用程式程式碼也必須要有相同的使用權限才能運作。 如果調用代碼沒有正確的許可權，則 作為代碼訪問安全<xref:System.Security.SecurityException>堆疊遍歷的結果將出現 。

## <a name="application-code-that-isnt-a-reusable-component"></a>不是可重用元件的應用程式代碼

如果代碼是其他代碼不會調用的應用程式的一部分，則安全性很簡單，並且可能不需要特殊編碼。 不過請記住，惡意程式碼可以呼叫您的程式碼。 雖然程式碼存取安全性可以制止惡意程式碼存取資源，這類的程式碼還是可以讀取可能含有敏感資訊的欄位或屬性的值。

此外，如果您的程式碼接受網際網路或其他不可靠來源的使用者輸入，您也必須小心惡意輸入。

## <a name="managed-wrapper-to-native-code-implementation"></a>託管包裝到本機代碼實現

在這個案例中，通常某些有用的功能是在您想提供給 Managed 程式碼的機器碼中所實作。 使用平台叫用或 COM Interop 就可輕鬆撰寫 Managed 包裝函式。 但是，如果您這麼做，包裝函式的呼叫端就必須具有 Unmanaged 程式碼的權限才會成功。 在預設策略下，這意味著從 Intranet 或 Internet 下載的代碼將不能與包裝器配合使用。

與其將非託管代碼許可權授予使用這些包裝器的所有應用程式，不如僅將這些許可權授予包裝代碼。 如果基礎功能未公開任何資源而且實作也一樣安全，包裝函式就只需要判斷它的權限，讓任何程式碼都可以透過它來呼叫。 當牽涉到資源時，安全性程式碼撰寫應該與下一章節說明的程式庫程式碼的狀況相同。 由於包裝函式對這些資源而言是可能公開的呼叫端，因此小心驗證機器碼安全性的程序是必要的，而且這個程序必須由包裝函式負責執行。

## <a name="library-code-that-exposes-protected-resources"></a>公開受保護資源的庫代碼

以下方法是安全編碼最強大且具有潛在危險（如果處理不正確）：您的庫充當其他代碼訪問某些不可用資源的介面，就像 .NET 類強制他們使用的資源的許可權。 不論您在何處公開資源，您的程式都必須先要求適用於資源的使用權限 (亦即它必須執行安全性檢查)，然後再判斷它的權限，以執行實際的作業。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[設定狀態資料的安全性](securing-state-data.md)|說明如何保護私用成員。|
|[安全性和使用者輸入](security-and-user-input.md)|描述接受使用者輸入之應用程式的安全性疑慮。|
|[安全性和競爭情形](security-and-race-conditions.md)|說明如何避免程式碼中的競爭情形。|
|[安全性和產生作業中的程式碼](security-and-on-the-fly-code-generation.md)|描述產生動態程式碼之應用程式的安全性疑慮。|
|[基於角色的安全性](role-based-security.md)|詳細介紹了基於 .NET 角色的安全性，並提供了在代碼中使用它的說明。|
