![Logo](admin/onvif_logo.png)
# ioBroker.onvif
=================

## ���������
1. ������� ��������� ��������
2. ������ ������ ������������ (������ ������)
3. ������ ����������� ��������� ��� �������� �� ���������
4. ������ START SCAN

���� ��� ������� ���������, � �������� ���� �������� �������� �������� ������ � ����� ��������� ������ ������ ����� ����������� ��������

## �������
������� ������������� ������������� �� ������� � ����������� �������.
�������, ������� ���������� ������, �������� � �������� ����:

```
onvif.0.192_168_1_4_80.message.tns1:RuleEngine/FieldDetector/ObjectsInside
onvif.0.192_168_1_4_80.message.tns1:VideoSource/MotionAlarm.State
```

## ������ ��������
��� ����� ������������ �������:
```
sendTo('onvif.0', command, message, callback);
```
������ ������� ��� ������� �������� � �������� � ��������:
```
const fs = require('fs');

function getSnapshot(caption){
    sendTo('onvif.0', 'saveFileSnapshot', {"id":"onvif.0.192_168_1_4_80", "file":"/opt/cameras/snapshot.jpg"}, (data) => {
        console.log('image ������: ' + data);
        if (data === "OK")
            sendTo('telegram.0', {text: '/opt/cameras/snapshot.jpg', caption: caption});
    });
}
```
*caption* - ��������� ��� �������� � ���������
�������� ����� ��� �� �������, ��� � �� ������/�����������
