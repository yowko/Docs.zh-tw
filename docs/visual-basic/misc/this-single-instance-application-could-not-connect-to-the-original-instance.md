---
title: "此單一執行個體應用程式無法連線到原始執行個體 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17a3ecd69e0e0974b2a8fc50090097b93dc0def3
ms.lasthandoff: 03/13/2017

---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>此單一執行個體應用程式無法連接到原始執行個體
此單一執行個體應用程式無法連接到原始執行個體。 此問題的部分可能原因如下：  
  
-   原始執行個體停止回應。  
  
-   應用程式沒有建立核心物件的權限。 如需核心物件的詳細資訊，請參閱[Mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)。  
  
     核心物件的主檔名 (Base Name) 是由連接組件的 GUID、主要版本號碼，以及次要版本號碼所組成。 例如，基底名稱可能是 `3639f15d-9547-43da-8145-60da347829915.1`。  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>在開發應用程式時更正這個錯誤  
  
1.  檢查應用程式並未進入沒有回應的狀態。  
  
2.  檢查應用程式有足夠的權限可建立核心物件。  
  
3.  重新啟動應用程式的原始執行個體。  
  
4.  重新啟動電腦，以針對連接到原始執行個體應用程式所需的資源，清除可能正在使用它的任何處理序。  
  
5.  記下錯誤發生時的情況，並致電 Microsoft 產品支援服務。  
  
## <a name="see-also"></a>另請參閱  
 [NIB: How to︰ 指定應用程式 (Visual Basic) 的執行個體行為](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [偵錯工具基本概念](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)   
 [PAVEOVER 產品支援和可及性](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
