---
title: "방법: PrintForm 구성 요소를 사용하여 폼 인쇄(Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5edad4f04b98dcf0dfa328f111db5dcb423036e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a>방법: PrintForm 구성 요소를 사용하여 폼 인쇄(Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 구성 요소를 사용하면 <xref:System.Drawing.Printing.PrintDocument> 구성 요소를 사용하지 않고 화면에 표시된 대로 정확히 폼 이미지를 빠르게 인쇄할 수 있습니다. 다음 절차에서는 프린터, 인쇄 미리 보기 창, Encapsulated PostScript 파일 등으로 폼을 인쇄하는 방법을 보여 줍니다.  
  
 PowerPack 컨트롤은 Visual Studio에 더 포함되지 않지만 [다운로드 센터](http://www.microsoft.com/en-us/download/details.aspx?id=25169)에서 다운로드할 수 있습니다.  
  
### <a name="to-print-a-form-to-the-default-printer"></a>폼을 기본 프린터로 인쇄하려면  
  
1.  **도구 상자**에서 **Visual Basic PowerPacks** 탭을 클릭하고 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 구성 요소를 폼으로 끕니다.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 구성 요소가 구성 요소 트레이에 추가됩니다.  
  
2.  **속성** 창에서 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 속성을 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>로 설정합니다.  
  
3.  `Click` 인쇄 **용**`Button`이벤트 처리기와 같은 적절한 이벤트 처리기에 다음 코드를 추가합니다.  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a>폼을 인쇄 미리 보기 창에 표시하려면  
  
1.  **도구 상자**에서 **Visual Basic PowerPacks** 탭을 클릭하고 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 구성 요소를 폼으로 끕니다.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 구성 요소가 구성 요소 트레이에 추가됩니다.  
  
2.  **속성** 창에서 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 속성을 <xref:System.Drawing.Printing.PrintAction.PrintToPreview>로 설정합니다.  
  
3.  `Click` 인쇄 **용**`Button`이벤트 처리기와 같은 적절한 이벤트 처리기에 다음 코드를 추가합니다.  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a>폼을 파일로 출력하려면  
  
1.  **도구 상자**에서 **Visual Basic PowerPacks** 탭을 클릭하고 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 구성 요소를 폼으로 끕니다.  
  
     <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 구성 요소가 구성 요소 트레이에 추가됩니다.  
  
2.  **속성** 창에서 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 속성을 <xref:System.Drawing.Printing.PrintAction.PrintToFile>로 설정합니다.  
  
3.  선택적으로 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> 속성을 선택하고 대상 파일의 전체 경로 및 파일 이름을 입력합니다.  
  
     이 단계를 건너뛰면 런타임에 파일 이름을 묻는 메시지가 사용자에게 표시됩니다.  
  
4.  `Click` 인쇄 **용**`Button`이벤트 처리기와 같은 적절한 이벤트 처리기에 다음 코드를 추가합니다.  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [방법: 폼의 클라이언트 영역 인쇄](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [방법: 폼의 클라이언트 영역 및 비클라이언트 영역 인쇄](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [방법: 스크롤 가능 폼 인쇄](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [PrintForm 구성 요소](../../../visual-basic/developing-apps/printing/printform-component.md)
