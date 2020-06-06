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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153811"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> 項目
指定未處理的工作例外狀況是否應終止執行中的處理序。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
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
|`enabled`|必要屬性。<br /><br /> 指定未處理的工作例外狀況是否應終止正在執行的進程。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會針對未處理的工作例外狀況終止正在執行的進程。 此為預設值。|  
|`true`|針對未處理的工作例外狀況終止正在執行的進程。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
|||  
  
## <a name="remarks"></a>備註  
 如果未觀察到與相關聯的例外狀況 <xref:System.Threading.Tasks.Task> ，則不會有任何作業 <xref:System.Threading.Tasks.Task.Wait%2A> 、父代未附加，且屬性未被 <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 讀取。工作例外狀況會被視為未觀察到。  
  
 在 .NET Framework 4 中，根據預設，如果已進行垃圾收集，則完成項會擲回 <xref:System.Threading.Tasks.Task> 例外狀況並終止進程。 進程的終止取決於垃圾收集和結束的時間。  
  
 為了讓開發人員更容易撰寫以工作為基礎的非同步程式碼，.NET Framework 4.5 會變更未觀察到例外狀況的這個預設行為。 未觀察到例外狀況仍然會 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 引發事件，但根據預設，進程不會終止。 而是在引發事件之後忽略例外狀況，而不論事件處理常式是否觀察到例外狀況。  
  
 在 .NET Framework 4.5 中，您可以使用應用程式佈建檔中的[ \<ThrowUnobservedTaskExceptions> 元素](throwunobservedtaskexceptions-element.md)，以啟用擲回例外狀況的 .NET Framework 4 行為。  
  
 您也可以利用下列其中一種方式來指定例外狀況行為：  
  
- 藉由設定環境變數 `COMPlus_ThrowUnobservedTaskExceptions` （ `set COMPlus_ThrowUnobservedTaskExceptions=1` ）。  
  
- 藉由在 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft 中設定 registry DWORD 值 ThrowUnobservedTaskExceptions = 1 \\ 。.Netframework 鍵。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用應用程式佈建檔來啟用工作中的例外狀況擲回。  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何從工作擲回未觀察到例外狀況。 程式碼必須以發行的程式的形式執行，才能正常運作。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
