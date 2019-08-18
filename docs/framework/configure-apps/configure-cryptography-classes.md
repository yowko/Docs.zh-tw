---
title: 設定密碼編譯類別
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567341"
---
# <a name="configuring-cryptography-classes"></a>設定密碼編譯類別
此 Windows SDK 可讓電腦系統管理員設定 .NET Framework 和適當撰寫的應用程式所使用的預設密碼編譯演算法和演算法實現。  例如, 擁有自己執行密碼編譯演算法的企業, 可以讓該執行成為預設值, 而不是在 Windows SDK 中隨附的執行。 雖然使用密碼編譯的受控應用程式一律會選擇明確系結至特定的執行, 但建議使用加密設定系統來建立密碼編譯物件。  
  
## <a name="in-this-section"></a>本節內容  
 [將演算法名稱對應至密碼編譯類別](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 說明如何將演算法名稱對應至密碼編譯類別。  
  
 [對應物件識別項至密碼編譯演算法](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 描述如何將物件識別碼對應至密碼編譯演算法。  
  
## <a name="related-sections"></a>相關章節  
 [The signature is valid](../../../docs/standard/security/cryptographic-services.md)  
 提供 Windows SDK 所提供的密碼編譯服務的總覽。  
  
 [密碼編譯設定結構描述](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。
