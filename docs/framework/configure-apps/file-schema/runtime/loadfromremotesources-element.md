---
title: <loadFromRemoteSources> 項目
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154058"
---
# <a name="loadfromremotesources-element"></a>\<負載從遠端源>元素
指定是否應授予從遠端源載入的程式集對 .NET 框架 4 和更高版本完全信任。
  
> [!NOTE]
> 如果您因為 Visual Studio 專案錯誤清單中的錯誤訊息或建置錯誤而被定向到本文，請參閱["如何：在視覺化工作室中的 Web 中使用程式集](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))"。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<負載從遠端源>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否應授予從遠端源載入的程式集完全信任。|  
  
## <a name="enabled-attribute"></a>啟用的屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不要對來自遠端源的應用程式授予完全信任。 這是預設值。|  
|`true`|完全信任來自遠端源的應用程式。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註

在 .NET Framework 3.5 和早期版本中，如果從遠端位置載入程式集，則程式集中的代碼將部分信任地運行，授予集取決於載入該程式集的區域。 例如，如果從網站載入程式集，則程式集將載入到 Internet 區域並授予 Internet 許可權集。 換句話說，它在一個互聯網沙箱中執行。

從 .NET 框架 4 開始，代碼訪問安全 （CAS） 策略被禁用，程式集完全信任地載入。 通常，這將完全信任載入以前已沙箱<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>的方法的程式集。 為了防止這種情況，預設情況下禁用在從遠端源載入的程式集中運行代碼的能力。 預設情況下，如果嘗試載入遠端程式集，則會引發如下所示的<xref:System.IO.FileLoadException>異常消息：

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

要載入程式集並執行其代碼，必須：

- 顯式為程式集創建沙箱（[請參閱如何：在沙箱中運行部分受信任的代碼](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)）。

- 完全信任運行程式集的代碼。 通過配置元素來`<loadFromRemoteSources>`執行此操作。 它允許您指定在 .NET Framework 的早期版本中以部分信任方式運行的程式集現在完全信任 .NET 框架 4 和更高版本。

> [!IMPORTANT]
> 如果程式集不應完全信任地運行，請不要設置此配置元素。 相反，請創建一個裝沙<xref:System.AppDomain>盒以載入程式集。

僅當`enabled`禁用代碼訪問`<loadFromRemoteSources>`安全性 （CAS） 時，元素的屬性才有效。 預設情況下，在 .NET 框架 4 和更高版本中禁用 CAS 策略。 如果設置為`enabled``true`，則遠端程式集將被授予完全信任。

如果未`enabled`設置為`true`，<xref:System.IO.FileLoadException>則 在以下任一條件下引發 ：

- 當前域的沙箱行為不同于其在 .NET 框架 3.5 中的行為。 這要求禁用 CAS 策略，並且當前域不得沙箱化。

- 正在載入的程式集不來自`MyComputer`區域。

設置元素`<loadFromRemoteSources>`以防止`true`引發此異常。 它使您能夠指定您不依賴通用語言運行時來對載入的程式集進行沙箱，以確保安全性，並且可以允許它們完全信任地執行。

## <a name="notes"></a>注意

- 在 .NET 框架 4.5 和更高版本中，本地網路共用上的程式集預設完全信任運行;您不必啟用該`<loadFromRemoteSources>`元素。

- 如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。 您可以通過更改其檔案屬性來更改該名稱，也可以使用 元素`<loadFromRemoteSources>`授予程式集完全信任。 或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。

- 您可以在 Windows<xref:System.IO.FileLoadException>虛擬 PC 應用程式中運行的 應用程式中獲取 。 當您嘗試從託管電腦上的連結資料夾中載入檔時，可能會發生這種情況。 當您嘗試從通過[遠端桌面服務](/windows/win32/termserv/terminal-services-portal)（終端服務）連結的資料夾中載入檔時，也會發生這種情況。 為了避免異常，請設置為`enabled``true`。

## <a name="configuration-file"></a>組態檔

此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。 有關詳細資訊，請參閱文章["CAS 策略的更多隱式使用：在](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources).NET 安全博客中載入從遠端資源"。  

## <a name="example"></a>範例

下面的示例演示如何對從遠端源載入的程式集授予完全信任。

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>另請參閱

- [CAS 策略的更多隱式使用：從遠端源載入](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [如何：在沙箱中執行部分信任的程式碼](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
