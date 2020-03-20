---
title: <ThrowUnobservedTaskExceptions> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153811"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<引發未觀察到的任務異常>元素
指定未處理的工作例外狀況是否應終止執行中的處理序。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<引發未觀察到的任務異常>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定未處理的任務異常是否應終止正在運行的進程。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不終止未處理的任務異常的運行進程。 這是預設值。|  
|`true`|終止未處理的任務異常的運行進程。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
|||  
  
## <a name="remarks"></a>備註  
 如果未觀察到與<xref:System.Threading.Tasks.Task>關聯的異常，則沒有<xref:System.Threading.Tasks.Task.Wait%2A>操作，父項未連接，並且<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>未讀取該屬性，則任務異常被視為未觀察到。  
  
 預設情況下，在 .NET 框架 4 中<xref:System.Threading.Tasks.Task>，如果正在回收具有未觀察到異常的 異常，則終端子將引發異常並終止進程。 流程的終止取決於垃圾回收和定稿的時間。  
  
 為了使開發人員更容易基於任務編寫非同步代碼，.NET Framework 4.5 會更改此預設行為，以進行未觀察到的異常。 未觀察到的異常仍會導致<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>引發事件，但預設情況下，進程不會終止。 相反，無論事件處理常式是否遵守異常，在引發事件後將忽略異常。  
  
 在 .NET 框架 4.5 中，可以使用應用程式佈建檔中的[\<ThrowUnununununtaskexception> 元素](throwunobservedtaskexceptions-element.md)來啟用引發異常的 .NET 框架 4 行為。  
  
 還可以通過以下方式之一指定異常行為：  
  
- 通過設置環境變數`COMPlus_ThrowUnobservedTaskExceptions`（。`set COMPlus_ThrowUnobservedTaskExceptions=1`  
  
- 通過設置註冊表 DWORD 值"ThrowUnunun_TaskExceptions " HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft\\中為 1。NETFramework 金鑰。  
  
## <a name="example"></a>範例  
 下面的示例演示如何通過使用應用程式佈建檔在任務中啟用異常的引發。  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>範例  
 下面的示例演示如何從任務中引發未觀察到的異常。 代碼必須作為已發佈的程式運行才能正常工作。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
