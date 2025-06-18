import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  final int userPoints = 125;

  @override
  Widget build(BuildContext context) {
    return Directionality(
      textDirection: TextDirection.rtl, // للغة العربية
      child: Scaffold(
        appBar: AppBar(
          title: Text("سنتات بلاس", style: TextStyle(color: Colors.white)),
          backgroundColor: Colors.amber[800],
          centerTitle: true,
        ),
        body: Container(
          padding: EdgeInsets.all(16),
          child: Column(
            children: [
              // الرصيد الحالي
              Container(
                padding: EdgeInsets.all(16),
                decoration: BoxDecoration(
                  color: Colors.amber[100],
                  borderRadius: BorderRadius.circular(15),
                ),
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.spaceBetween,
                  children: [
                    Text("رصيدك الحالي:", style: TextStyle(fontSize: 20)),
                    Text("$userPoints نقطة", style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold)),
                  ],
                ),
              ),

              SizedBox(height: 30),

              // زر عجلة الحظ
              ElevatedButton(
                onPressed: () {
                  Navigator.pushNamed(context, '/wheel');
                },
                style: ElevatedButton.styleFrom(
                  backgroundColor: Colors.amber[800],
                  padding: EdgeInsets.symmetric(vertical: 16, horizontal: 32),
                  shape: RoundedRectangleBorder(borderRadius: BorderRadius.circular(30)),
                ),
                child: Text("🎡 دوّر عجلة الحظ", style: TextStyle(fontSize: 22)),
              ),

              SizedBox(height: 40),

              // المهام اليومية
              Text("المهام اليومية", style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold)),
              SizedBox(height: 10),
              Row(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: [
                  taskCard("شاهد إعلان", Icons.play_circle_fill),
                  taskCard("دعوة صديق", Icons.person_add_alt_1),
                  taskCard("تنزيل تطبيق", Icons.download),
                ],
              ),

              Spacer(),

              // سحب الأرباح
              ElevatedButton.icon(
                onPressed: () {
                  Navigator.pushNamed(context, '/withdraw');
                },
                icon: Icon(Icons.attach_money),
                label: Text("سحب الأرباح", style: TextStyle(fontSize: 18)),
                style: ElevatedButton.styleFrom(
                  backgroundColor: Colors.green,
                  padding: EdgeInsets.symmetric(vertical: 14, horizontal: 24),
                ),
              )
            ],
          ),
        ),
      ),
    );
  }

  Widget taskCard(String title, IconData icon) {
    return Column(
      children: [
        CircleAvatar(
          radius: 30,
          backgroundColor: Colors.amber[300],
          child: Icon(icon, size: 30, color: Colors.white),
        ),
        SizedBox(height: 5),
        Text(title, style: TextStyle(fontSize: 14)),
      ],
    );
  }
}
