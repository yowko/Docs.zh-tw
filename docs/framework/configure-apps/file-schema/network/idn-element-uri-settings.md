---
title: <idn> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698165"
---
# <a name="idn-element-uri-settings"></a>@no__t 0idn > 元素（Uri 設定）

指定是否要將國際化功能變數名稱（IDN）剖析套用至功能變數名稱。
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<idn >**  
  
## <a name="syntax"></a>語法  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  

|**目**|**描述**|  
|-----------------|---------------------|  
|`enabled`|指定是否將國際化功能變數名稱（IDN）剖析套用至功能變數名稱，預設值為 none。|  

### <a name="child-elements"></a>子元素

None
  
### <a name="parent-elements"></a>父元素

|**目**|**描述**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。|  

## <a name="remarks"></a>備註

現有的 <xref:System.Uri> 類別已在 .NET Framework 3.5 中擴充。 3.0 SP1 和 2.0 SP1，支援國際資源識別碼（IRI）和國際化功能變數名稱（IDN）。 目前的使用者除非特別啟用 IRI 和 IDN 支援，否則不會看到 .NET Framework 2.0 行為的任何變更。 這可確保應用程式與舊版 .NET framework 相容。

若要啟用對 IRI 的支援，必須進行下列兩項變更：

1. 將下面這一行新增至 machine.config 檔案的 .NET Framework 2.0 目錄底下：
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. 指定是否要套用至功能變數名稱的國際化功能變數名稱（IDN）剖析，以及是否應該套用 IRI 剖析規則。 此作業可在 machine.config 或 app.config 檔案中完成。

 根據所使用的 DNS 伺服器，IDN 有三個可能的值：

- 已啟用 idn = 全部  

     這個值會將任何 Unicode 功能變數名稱轉換成其 Punycode 對應項（IDN 名稱）。

- 已啟用 idn = AllExceptIntranet

     這個值會將不在近端內部網路上的所有 Unicode 功能變數名稱轉換成使用 Punycode 對等專案（IDN 名稱）。 在此情況下，若要處理近端內部網路上的國際名稱，用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。

- 已啟用 idn = 無

     這個值不會將任何 Unicode 功能變數名稱轉換成使用 Punycode。 這是與 .NET Framework 2.0 行為一致的預設值。

 啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。 Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。 這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。

### <a name="configuration-files"></a>組態檔

此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。

## <a name="example"></a>範例

下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定：

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
