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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b12d5d95a17439308d79d094e8c22206778f3128
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-cryptography-classes"></a>設定密碼編譯類別
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]讓電腦系統管理員設定的預設密碼編譯演算法和.NET Framework 和適當地撰寫應用程式使用的演算法實作。  比方說，有自己的密碼編譯演算法實作的企業可以進行實作的預設值，而不是隨附於實作[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]。 雖然使用密碼編譯的 managed 應用程式可以隨時明確繫結至特定的實作，但建議他們使用密碼編譯組態系統建立密碼編譯物件。  
  
## <a name="in-this-section"></a>本節內容  
 [將演算法名稱對應至密碼編譯類別](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 描述如何將演算法名稱對應至密碼編譯類別。  
  
 [對應物件識別項至密碼編譯演算法](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 描述如何將物件識別碼對應至密碼編譯演算法。  
  
## <a name="related-sections"></a>相關章節  
 [The signature is valid](../../../docs/standard/security/cryptographic-services.md)  
 提供的密碼編譯服務提供的概觀[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]。  
  
 [密碼編譯設定結構描述](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。
