---
title: "방법: 자동으로 생성된 열을 Windows Forms DataGridView 컨트롤에서 제거"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], removing columns
- columns [Windows Forms], removing
ms.assetid: 92e28d98-95a3-446c-9150-41b7c7e5be15
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04375c89e80acb079f4862c159583adb4b0e4ca1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-autogenerated-columns-from-a-windows-forms-datagridview-control"></a>방법: 자동으로 생성된 열을 Windows Forms DataGridView 컨트롤에서 제거
경우에 <xref:System.Windows.Forms.DataGridView> 컨트롤이 해당 데이터 원본에서 데이터를 기반으로 해당 열 자동 생성 하도록 설정 되어, 특정 열을 선택적으로 생략할 수 있습니다. 호출 하 여이 작업을 수행할 수는 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> 에서 메서드는 <xref:System.Windows.Forms.DataGridView.Columns%2A> 컬렉션입니다. 설정 하 여 보기에서 열을 숨길 수 또는 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 속성을 `false`합니다. 이 방법은 특정 조건에 숨겨진된 열을 표시 하려는 경우 또는 표시 하지 않고 열의 데이터에 액세스 해야 할 때 유용 합니다.  
  
### <a name="to-remove-autogenerated-columns"></a>자동 생성 된 열을 제거 하려면  
  
-   호출의 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> 에서 메서드는 <xref:System.Windows.Forms.DataGridView.Columns%2A> 컬렉션입니다.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#111)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#111)]  
  
### <a name="to-hide-autogenerated-columns"></a>자동 생성 된 열을 숨기려면  
  
-   열의 설정 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 속성을 `false`합니다.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#112)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#112)]  
  
## <a name="example"></a>예제  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#110)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#110)]  
  
## <a name="compiling-the-code"></a>코드 컴파일  
 이 예제에는 다음 사항이 필요합니다.  
  
-   A <xref:System.Windows.Forms.DataGridView> 라는 컨트롤 `dataGridView1` 포함 된 테이블에 바인딩된 `Fax` 및 `CustomerID` 열 같은 `Customers` Northwind 샘플 데이터베이스의 테이블입니다.  
  
-   <xref:System?displayProperty=nameWithType> 및 <xref:System.Windows.Forms?displayProperty=nameWithType> 어셈블리에 대한 참조  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView 컨트롤에서 데이터 표시](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
