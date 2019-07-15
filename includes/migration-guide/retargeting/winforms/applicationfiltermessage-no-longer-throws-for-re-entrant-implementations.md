---
ms.openlocfilehash: 8e37007318a55188d44607fd5e4c4f3950c105df
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804385"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>針對 IMessageFilter.PreFilterMessage 的可重新進入實作，Application.FilterMessage 不會再擲回例外狀況

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.1 之前，使用呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> 或 <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> 的 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 呼叫 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> (同時也呼叫<xref:System.Windows.Forms.Application.DoEvents>) 會造成 <xref:System.IndexOutOfRangeException?displayProperty=name>。<p/>從目標為 .NET Framework 4.6.1 的應用程式開始，不會再擲回此例外狀況，而且可能會使用如上所述的可重新進入篩選。|
|建議|請注意，<xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> 將不再針對上述的可重新進入 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 行為進行擲回。 這只會影響以 .NET Framework 4.6.1 為目標的應用程式。藉由使用 [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) 相容性參數，以 .NET Framework 4.6.1 為目標的應用程式可退出這項變更 (或以舊版 Framework 為目標的應用程式可加入這項變更)。|
|範圍|Edge|
|版本|4.6.1|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

