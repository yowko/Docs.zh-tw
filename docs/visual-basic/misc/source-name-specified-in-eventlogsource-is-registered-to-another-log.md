---
title: 在 EventLogSource 中指定的來源名稱會登錄到不在 EventLogName 指定的記錄檔
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: dc4c8f212de61a304f04c81d81d2e75c490450ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33638591"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>在 EventLogSource 中指定的來源名稱會登錄到不在 EventLogName 指定的記錄檔
`EventLog` 嘗試參考登錄到不同記錄檔的來源。 如果要將項目寫入事件記錄檔，您必須指定 <xref:System.Diagnostics.EventLog.Source%2A> 屬性。 <xref:System.Diagnostics.EventLog.Source%2A> 屬性會將元件和事件記錄登錄為有效的項目來源。 單一來源一次只能和一筆事件記錄建立關聯 (因此寫入項目)。  
  
 根據預設，如果您嘗試寫入項目，卻沒有先將元件登錄為有效的來源，系統會使用 <xref:System.Diagnostics.EventLog.Source%2A> 屬性的值當做來源字串，自動登錄來源和事件記錄。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定來源已登錄到正確的記錄檔。 若要這樣做，請使用 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 方法或其多載之一，指定可向事件記錄檔唯一識別元件的字串。  
  
## <a name="see-also"></a>另請參閱  
 [管理事件記錄檔](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [事件記錄檔參考](http://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [如何： 加入您的應用程式事件記錄檔項目的來源](http://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [如何： 移除的事件來源](http://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
