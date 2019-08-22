---
title: 密碼編譯設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a2aa56f8b2a92f906293adfae9d23ed8959336fb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664288"
---
# <a name="cryptography-settings-schema"></a>密碼編譯設定結構描述
密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。  
  
 [ **\<configuration>** ](../configuration-element.md)  
  
 [ **\<mscorlib>** ](mscorlib-element-for-cryptography-settings.md)  
  
 [ **\<cryptographySettings>** ](cryptographysettings-element.md)  
  
 [ **\<cryptoNameMapping>** ](cryptonamemapping-element.md)  
  
 [ **\<cryptoClasses>** ](cryptoclasses-element.md)  
  
 [ **\<cryptoClass>** ](cryptoclass-element.md)  
  
 [ **\<nameEntry>** ](nameentry-element.md)  
  
 [ **\<oidMap>** ](oidmap-element.md)  
  
 [ **\<oidEntry>** ](oidentry-element.md)  
  
|項目|描述|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。|  
|[ **\<cryptographySettings**>](cryptographysettings-element.md)|包含密碼編譯設定。|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|包含易記名稱的類別對應。|  
|[密碼編譯設定的 **\<mscorlib>** 項目](mscorlib-element-for-cryptography-settings.md)|包含 **\<cryptographySettings>** 項目。|  
|[ **\<nameEntry>** ](nameentry-element.md)|將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。|  
|[ **\<oidEntry>** ](oidentry-element.md)|將 ASN.1 物件識別碼 (OID) 對應至易記名稱。|  
|[ **\<oidMap>** ](oidmap-element.md)|包含類別的 ASN.1 OID 對應。|  
  
## <a name="see-also"></a>另請參閱

- [組態檔結構描述](../index.md)
- [The signature is valid](../../../../../docs/standard/security/cryptographic-services.md)
