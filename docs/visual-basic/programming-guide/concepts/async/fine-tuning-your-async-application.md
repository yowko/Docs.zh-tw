---
title: "微調非同步應用程式 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d0cac2fe7305031b93a375a08e785285a291320
ms.lasthandoff: 03/13/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a>微調非同步應用程式 (Visual Basic)
您可以加入有效位數和彈性非同步應用程式所使用的方法和屬性，<xref:System.Threading.Tasks.Task>可產生型別。</xref:System.Threading.Tasks.Task> 本章節的主題說明使用範例<xref:System.Threading.CancellationToken>重要`Task`方法，例如<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>和<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> </xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> </xref:System.Threading.CancellationToken>  
  
 使用`WhenAny`和`WhenAll`，您可以更輕鬆地啟動多項工作，並藉由監視單一工作等候其完成。  
  
-   `WhenAny`傳回集合中的任何工作完成時完成的工作。  
  
     如需使用範例`WhenAny`，請參閱[後一個完整 (Visual Basic) 取消剩餘的非同步工作](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)和[啟動多項非同步工作和程序它們做為它們完成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)。  
  
-   `WhenAll`傳回集合中的所有工作都都完成時完成的工作。  
  
     如需詳細資訊和範例會使用`WhenAll`，請參閱[How to︰ 擴充非同步逐步解說使用 Task.WhenAll (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。  
  
 本節包含下列的範例。  
  
-   [取消一項非同步工作或一份工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)。  
  
-   [取消非同步工作一段時間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [當取消剩餘的非同步工作是完整 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [啟動多項非同步工作並處理它們完成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。  
  
 專案會建立包含啟動處理序的按鈕和一個按鈕，取消它，如下列影像所示的 UI。 這些按鈕會命名為`startButton`和`cancelButton`。  
  
 ![具有 [取消] 按鈕的 WPF 視窗](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "取消")  
  
 您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。  
  
## <a name="see-also"></a>另請參閱  
 [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
