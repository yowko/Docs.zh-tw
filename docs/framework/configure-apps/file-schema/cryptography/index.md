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
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087998"
---
# <a name="cryptography-settings-schema"></a>密碼編譯設定結構描述
密碼編譯設定結構描述包含指定如何將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|元素|描述|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|包含在專案中有易記名稱對應的密碼編譯類別清單 **\<nameEntry>** 。|  
|[**\<cryptoClass**>](cryptoclass-element.md)|包含在專案中具有易記名稱對應的密碼編譯類別 **\<nameEntry>** 。|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|包含密碼編譯設定。|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|包含易記名稱的類別對應。|  
|[**\<mscorlib>** 密碼編譯設定的元素](mscorlib-element-for-cryptography-settings.md)|包含 **\<cryptographySettings>** 元素。|  
|[**\<nameEntry>**](nameentry-element.md)|將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。|  
|[**\<oidEntry>**](oidentry-element.md)|將 ASN.1 物件識別碼 (OID) 對應至易記名稱。|  
|[**\<oidMap>**](oidmap-element.md)|包含類別的 ASN.1 OID 對應。|  
  
## <a name="see-also"></a>另請參閱

- [設定檔架構](../index.md)
- [密碼編譯服務](../../../../standard/security/cryptographic-services.md)
