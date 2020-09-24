---
title: 設定密碼編譯類別
description: 瞭解電腦系統管理員如何設定 .NET 和應用程式所使用的預設密碼編譯演算法和演算法實作為。
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 5262dfca914fd5306297ea9535bcef3d2088d107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165204"
---
# <a name="configuring-cryptography-classes"></a>設定密碼編譯類別

Windows SDK 可讓電腦系統管理員設定 .NET Framework 和適當撰寫的應用程式所使用的預設密碼編譯演算法和演算法執行。  例如，具有自己的密碼編譯演算法執行的企業，可以使該執行成為預設值，而不是 Windows SDK 中所附的實作為。 雖然使用加密的受控應用程式一律可以選擇明確地系結至特定的執行，但建議使用加密設定系統建立密碼編譯物件。  
  
## <a name="in-this-section"></a>本節內容  

 [將演算法名稱對應至密碼編譯類別](map-algorithm-names-to-cryptography-classes.md)  
 說明如何將演算法名稱對應至密碼編譯類別。  
  
 [對應物件識別項至密碼編譯演算法](map-object-identifiers-to-cryptography-algorithms.md)  
 描述如何將物件識別碼對應至密碼編譯演算法。  
  
## <a name="related-sections"></a>相關章節  

 [密碼編譯服務](../../standard/security/cryptographic-services.md)  
 概要說明 Windows SDK 所提供的密碼編譯服務。  
  
 [密碼編譯設定架構](./file-schema/cryptography/index.md)  
 說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。
