---
ms.openlocfilehash: 9b184f54650d2efb31ec66f443198b19ceaeb5f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614345"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>針對 IMessageFilter.PreFilterMessage 的可重新進入實作，Application.FilterMessage 不會再擲回例外狀況

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.1 之前，使用呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> 或 <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> 的 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 呼叫 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> (同時也呼叫<xref:System.Windows.Forms.Application.DoEvents>) 會造成 <xref:System.IndexOutOfRangeException?displayProperty=fullName>。<p/>從目標為 .NET Framework 4.6.1 的應用程式開始，不會再擲回此例外狀況，而且可能會使用如上所述的可重新進入篩選。

#### <a name="suggestion"></a>建議

請注意，<xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> 將不再針對上述的可重新進入 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 行為進行擲回。 這只會影響以 .NET Framework 4.6.1 為目標的應用程式。藉由使用 [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) 相容性參數，以 .NET Framework 4.6.1 為目標的應用程式可退出這項變更 (或以舊版 Framework 為目標的應用程式可加入這項變更)。

| 名稱          | 值       |
|:--------------|:------------|
| 影響範圍         | Edge        |
| 版本       | 4.6.1       |
| 類型          | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType>
