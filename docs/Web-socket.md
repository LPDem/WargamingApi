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
1. **SavaVisiblePositions**
  Для сохранения какие позиции видет пользователь. Если приходит новое старые    перезаписывается. **payload** ```number[]```


2. **PositionEditingStart** -- 
  Кто-то начал редактировать позициию.
  
    payload       
  `{iPositionId: sUsername}`
  
    example
  `{1:"Dmitry Kirol"}`


3. **PositionEditingEnd** закончил редактироват
    payload     
  `{iPositionId: Position}`

4. **NewPositionAdded**
  Добавлено новая позиция
    payload     
    `Position`

5. **PositionCommentNotification**
  Уведомление о новом коментарии
    payload:

    `{
        iId: number;
        iPositionId: number;
        sPositionName: string;
        sUserName: string;
        bUnread: boolean;
        sDate: string;
    }`

6. **PositionCommentNotificationMarkRead**
  payload:
  `iId: number;`

7. **PlanUpdatedNotification**

    payload:
    
    `{
      iId: number;
      sPlanName: string;
      sUserName: string;
      bUnread: boolean;
      sDate: string;
    }`

8. **PlanUpdatedNotificationMarkRead**
  payload:
  `iId: number;`

