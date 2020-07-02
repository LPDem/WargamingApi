# Web-socket comands

Общий формат всех сообщении:
```json json_schema
{
  "type": "object",
  "properties": {
    "type": {
      "type": "string",
      "description": "Тип сообщении"
    },
    "payload": {
      "type": string,
      "description": "Полезная нагрузка, все данные перед отправкой сконвертировать в json"
    }
  }
}
```

## Типы сообщении
1. **SaveVisiblePositions**
  Для сохранения какие позиции видет пользователь. Если приходит новое старые    перезаписывается. Отправляется от клиента к серверу
  
    payload: ```number[]```

2. **IStartedEditing** Пользователь который отправил сообщение начал редактировать позицию. Передает id позиции. Отправляется от клиента к серверу.

    payload: ```number```

3. **PositionEditingStart**  Кто-то начал редактировать позициию. Отправляется от сервера к клиенту
  
    payload:

    `{
      iPositionId: number,
      sUserName: string
    }`

4. **IFinishedEditing** Пользователь который отправил сообщение закончил редактировать позицию. Поле `changed` означает была ли позиция изменена или нет. Отправляется от клиента к серверу

    payload: 

    `{
      iPositionId: number,
      changed: boolean
    }`

5. **PositionEditingEnd** Кто-то закончил редактироват
   позицию. Поле `position` необязательная, передается только если позиция изменена. Отправляется от сервера к клиенту

    payload:

    `{
      iPositionId: number,
      position: Position
    }`
