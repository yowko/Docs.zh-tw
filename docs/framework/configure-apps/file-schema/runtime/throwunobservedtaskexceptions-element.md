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
ms.openlocfilehash: 012c2e70e66015bc317606a7eea07812b5df26e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183919"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> 項目

指定未處理的工作例外狀況是否應終止執行中的處理序。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定未處理的工作例外狀況是否應該終止正在執行的進程。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會針對未處理的工作例外狀況終止正在執行的進程。 此為預設值。|  
|`true`|針對未處理的工作例外狀況終止執行中的進程。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
|||  
  
## <a name="remarks"></a>備註  

 如果未觀察到與 a 相關聯的例外狀況 <xref:System.Threading.Tasks.Task> ，則不會執行任何作業 <xref:System.Threading.Tasks.Task.Wait%2A> ，父系也不會附加，且不會讀取此屬性，而會將 <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 工作例外狀況視為未觀察到。  
  
 在 .NET Framework 4 中，根據預設，如果 <xref:System.Threading.Tasks.Task> 有未觀察到例外狀況的已進行垃圾收集，完成項會擲回例外狀況並結束進程。 進程終止是由垃圾收集和結束時間所決定。  
  
 為了讓開發人員能更輕鬆地根據工作撰寫非同步程式碼，.NET Framework 4.5 會變更未觀察到例外狀況的這個預設行為。 未觀察到例外狀況仍然會 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 引發事件，但預設不會終止進程。 相反地，不論事件處理常式是否觀察到例外狀況，都會在引發事件之後忽略例外狀況。  
  
 在 .NET Framework 4.5 中，您可以使用應用程式佈建[ \<ThrowUnobservedTaskExceptions> 檔中的](throwunobservedtaskexceptions-element.md)專案，啟用擲回例外狀況的 .NET Framework 4 行為。  
  
 您也可以透過下列其中一種方式來指定例外狀況行為：  
  
- 藉由設定環境變數 `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`) 。  
  
- 藉由在 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft 中設定 registry DWORD 值 ThrowUnobservedTaskExceptions = 1 \\ 。.Netframework 鍵。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用應用程式佈建檔，啟用在工作中擲回例外狀況。  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>範例  

 下列範例示範如何從工作擲回未觀察到例外狀況。 程式碼必須以已發行的程式執行，才能正確運作。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
