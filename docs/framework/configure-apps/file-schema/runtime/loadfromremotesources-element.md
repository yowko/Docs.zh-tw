---
title: <loadFromRemoteSources> 項目
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83980d315c83aa5cc23944dbd271c29e0ed83206
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252472"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources > 元素
指定是否應將 .NET Framework 4 和更新版本中的完全信任授與從遠端來源載入的元件。
  
> [!NOTE]
> 如果您因為 Visual Studio 專案錯誤清單中的錯誤訊息或組建錯誤而被導向本文，請參閱[如何：在 Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))中使用來自 Web 的元件。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<loadFromRemoteSources >**  
  
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
|`enabled`|必要屬性。<br /><br /> 指定是否應授與從遠端來源載入的元件完全信任。|  
  
## <a name="enabled-attribute"></a>enabled 屬性  
  
|值|說明|  
|-----------|-----------------|  
|`false`|請勿將完全信任授與遠端來源的應用程式。 這是預設值。|  
|`true`|授與從遠端來源對應用程式的完全信任。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註

在 .NET Framework 3.5 和更早版本中，如果您從遠端位置載入元件，則元件中的程式碼會以部分信任的方式執行，而該授權集是根據載入它的區域而定。 例如，如果您從網站載入元件，則會將它載入至網際網路區域並授與網際網路許可權集合。 換句話說，它會在網際網路沙箱中執行。

從 .NET Framework 4 開始，會停用代碼啟用安全性（CAS）原則，並以完全信任的方式載入元件。 一般來說，這會授與完全信任給以先前已<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>沙箱化的方法所載入的元件。 為了避免這種情況，預設會停用在從遠端來源載入的元件中執行程式碼的功能。 根據預設，如果您嘗試載入遠端元件， <xref:System.IO.FileLoadException>則會擲回具有類似如下的例外狀況訊息：

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

若要載入元件並執行其程式碼，您必須執行下列其中一項：

- 明確建立元件的沙箱（請參閱[如何：在沙箱](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)中執行部分信任的程式碼）。

- 以完全信任的方式執行元件的程式碼。 您可以藉由設定`<loadFromRemoteSources>`元素來完成此動作。 它可讓您指定在舊版 .NET Framework 中以部分信任方式執行的元件，現在會在 .NET Framework 4 和更新版本中以完全信任的方式執行。

> [!IMPORTANT]
> 如果元件不應在完全信任中執行，請不要設定此 configuration 元素。 相反地，請建立<xref:System.AppDomain>用來載入元件的沙箱。

只有`enabled`在停用`<loadFromRemoteSources>`代碼啟用安全性（CAS）時，元素的屬性才有效。 預設會停用 .NET Framework 4 和更新版本中的 CAS 原則。 如果您將`enabled`設定`true`為，遠端元件會被授與完全信任。

如果`enabled`未設定為`true`， <xref:System.IO.FileLoadException>則會在下列任一情況下擲回：

- 目前網域的沙箱行為與其在 .NET Framework 3.5 中的行為不同。 這需要停用 CAS 原則，而目前的網域則不會進行沙箱處理。

- 正在載入的元件不是來自`MyComputer`區域。

設定元素以`true`防止擲回這個例外狀況。 `<loadFromRemoteSources>` 它可讓您指定您不依賴 common language runtime 將載入的元件沙箱處理為安全性，而且可以允許在完全信任的情況下執行。

## <a name="notes"></a>注意

- 在 .NET Framework 4.5 和更新版本中，本機網路共用上的元件預設會以完全信任的方式執行;您不需要啟用`<loadFromRemoteSources>`元素。

- 如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。 您可以藉由變更其檔案屬性來變更該指定，也可以使用`<loadFromRemoteSources>`元素來授與元件完全信任。 或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。

- 您可能會<xref:System.IO.FileLoadException>在 Windows 虛擬 PC 應用程式中執行的應用程式中取得。 當您嘗試從主控電腦上的連結資料夾載入檔案時，就會發生這種情況。 當您嘗試從連結于[遠端桌面服務](https://go.microsoft.com/fwlink/?LinkId=182775)（終端機服務）的資料夾載入檔案時，也可能會發生此問題。 若要避免例外狀況， `enabled`請`true`將設定為。

## <a name="configuration-file"></a>組態檔

此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。 如需詳細資訊，請參閱 .NET 安全性 blog 中的 < [CAS 原則的更多隱含用法： loadFromRemoteSources 一](https://go.microsoft.com/fwlink/p/?LinkId=266839)文。  

## <a name="example"></a>範例

下列範例顯示如何將完全信任授與從遠端來源載入的元件。

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>另請參閱

- [CAS 原則的更多隱含用法： loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [如何：在沙箱中執行部分信任的程式碼](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
