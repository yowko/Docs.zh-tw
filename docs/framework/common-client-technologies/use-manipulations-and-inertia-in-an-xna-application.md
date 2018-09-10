---
title: 在 XNA 應用程式中使用操作和慣性
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44248900"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>在 XNA 應用程式中使用操作和慣性
本文說明如何在 Microsoft XNA 應用程式中使用操作和慣性處理，來控制遊戲個件的移動。 在閱讀本文之前，您應該先熟悉[操作和慣性概觀](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)主題和基本 XNA 程式設計概念。  
  
 若要執行本文描述的工作，您的 XNA 專案必須參考 <xref:System.Windows.Input.Manipulations> 組件，而您的電腦上必須安裝 [XNA Game Studio](https://msdn.microsoft.com/library/bb200104.aspx) ([下載](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en))，以便專案可以參考 XNA 組件。  
  
## <a name="overview-of-functionality"></a>功能概觀  
 本文示範如何建立代表使用操作和慣性處理之遊戲個件的自訂類別。 這個類別可讓您透過使用滑鼠拖曳再放開的方式，在畫面上操作遊戲個件。 放開滑鼠之後，慣性處理會讓遊戲個件保持移動，但速度會逐漸變慢。 移動方式包括線性移動和角度移動。  
  
 ![簡單的操作和慣性應用。](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 此外，您可以建立管理多個遊戲個件的自訂集合。 這樣做會簡化 XNA Game 類別所需的處理。  
  
 [建立 GamePiece 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [建立 GamePieceCollection 類別](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [建立 Game1 類別](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [完整程式碼清單](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Input.Manipulations>  
 [操作和慣性概觀](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
