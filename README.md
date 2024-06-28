# How to limit custom colors to cells in the selected row in Flutter DataTable (SfDataGrid)?

In this article, we will show you how to limit custom colors to cells in the selected row in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all the necessary properties. To limit the custom color to cells in the selected row, the [buildRow](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/buildRow.html) method is called whenever a selection is made. You should verify if the row is part of the selected row collection using [DataGridController.SelectedRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridController/selectedRows.html).

```dart
 @override
  DataGridRowAdapter buildRow(DataGridRow row) {
    return DataGridRowAdapter(
        cells: row.getCells().map<Widget>((e) {
      Color? getColor() {
        if (!controller.selectedRows.contains(row)) {
          if (e.columnName == 'designation') {
            if (e.value == 'Developer') {
              return Colors.tealAccent;
            } else if (e.value == 'Manager') {
              return Colors.blue[200]!;
            }
          }
        }
        return null;
      }

      return Container(
        color: getColor(),
        alignment: Alignment.center,
        padding: const EdgeInsets.all(8.0),
        child: Text(e.value.toString()),
      );
    }).toList());
  }
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-limit-custom-colors-to-cells-in-the-selected-row-in-Flutter-DataTable).