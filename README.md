# my-flutter-app
My first Flutter application
flutter_app
import 'package:flutter/material.dart';
import 'package:url_launcher/url_launcher.dart';
import 'package:share_plus/share_plus.dart';

void main() {
  runApp(AgriculturalGuideApp());
}

class AgriculturalGuideApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'المرشد الزراعي المتكامل',
      theme: ThemeData(
        primarySwatch: Colors.green,
        fontFamily: 'Tajawal',
        useMaterial3: true,
      ),
      debugShowCheckedModeBanner: false,
      home: MainHomeScreen(),
    );
  }
}

// ==================== بيانات التطبيق ====================
class AppData {
  static const String supportWhatsApp = '+967734750438';
  static const String supportEmail = 'mmasa197911282017@gmail.com';
  
  // ========== 20 محصول جديد متنوع ==========
  static List<Map<String, dynamic>> crops = [
    {
      'id': 1,
      'name': 'قمح',
      'icon': Icons.grass,
      'color': Colors.amber,
      'season': 'شتوي',
      'water': 'متوسط',
      'soil': 'طميية جيدة الصرف',
      'temp': '15-25°م',
      'harvest': '4-6 شهور',
      'diseases': ['صدأ الأوراق', 'التفحم', 'أمراض الجذور'],
      'fertilizers': ['سوبر فوسفات', 'يوريا', 'كبريت زراعي'],
      'description': 'المحصول الاستراتيجي الرئيسي، يحتاج تربة خصبة وإضاءة جيدة',
    },
    {
      'id': 2,
      'name': 'ذرة',
      'icon': Icons.eco,
      'color': Colors.yellow,
      'season': 'صيفي',
      'water': 'كثير',
      'soil': 'طينية رملية',
      'temp': '20-30°م',
      'harvest': '3-4 شهور',
      'diseases': ['تبقع الأوراق', 'عفن الساق', 'لفحة الذرة'],
      'fertilizers': ['نترات الأمونيوم', 'سماد مركب NPK'],
      'description': 'محصول صيفي مهم للعلف والاستهلاك البشري',
    },
    {
      'id': 3,
      'name': 'طماطم',
      'icon': Icons.spa,
      'color': Colors.red,
      'season': 'صيفي',
      'water': 'كثير',
      'soil': 'رملية طينية',
      'temp': '18-27°م',
      'harvest': '70-90 يوم',
      'diseases': ['الندوة المتأخرة', 'العفن', 'فيروس تبرقش'],
      'fertilizers': ['سلفات البوتاسيوم', 'سماد عضوي'],
      'description': 'من أكثر الخضروات استهلاكاً، حساس للصقيع',
    },
    {
      'id': 4,
      'name': 'بطاطس',
      'icon': Icons.park,
      'color': Colors.brown,
      'season': 'شتوي',
      'water': 'متوسط',
      'soil': 'خفيفة جيدة الصرف',
      'temp': '15-20°م',
      'harvest': '3-4 شهور',
      'diseases': ['اللفحة', 'الجرب', 'العفن الجاف'],
      'fertilizers': ['سوبر فوسفات', 'سماد بوتاسي'],
      'description': 'محصول درني يحتاج تربة عميقة وباردة',
    },
    {
      'id': 5,
      'name': 'قات',
      'icon': Icons.forest,
      'color': Colors.green,
      'season': 'طوال السنة',
      'water': 'قليل',
      'soil': 'مرتفعات جبلية',
      'temp': '15-25°م',
      'harvest': 'مستمر',
      'diseases': ['حفار الساق', 'بق المكنسة', 'الأكاروسات'],
      'fertilizers': ['سماد عضوي', 'سلفات الأمونيوم'],
      'description': 'نبات معمر يزرع في المرتفعات، يحتاج عناية مستمرة',
    },
    {
      'id': 6,
      'name': 'بن',
      'icon': Icons.local_cafe,
      'color': Colors.brown,
      'season': 'طوال السنة',
      'water': 'متوسط',
      'soil': 'مرتفعات بركانية',
      'temp': '15-24°م',
      'harvest': 'مرة سنوياً',
      'diseases': ['صدأ الأوراق', 'دودة الثمار', 'لفحة الأوراق'],
      'fertilizers': ['سماد عضوي', 'سماد متوازن'],
      'description': 'محصول استوائي يحتاج ظل وتدرج حراري',
    },
    {
      'id': 7,
      'name': 'عنب',
      'icon': Icons.vineyard,
      'color': Colors.purple,
      'season': 'معتدل',
      'water': 'قليل',
      'soil': 'جيرية جيدة الصرف',
      'temp': '15-30°م',
      'harvest': 'صيفي',
      'diseases': ['عفن الثمار', 'بياض دقيقي', 'حشرة المن'],
      'fertilizers': ['سوبر فوسفات', 'سماد بورون'],
      'description': 'فاكهة متسلقة تحتاج دعم وتقليم مستمر',
    },
    {
      'id': 8,
      'name': 'موز',
      'icon': Icons.forest,
      'color': Colors.yellow,
      'season': 'استوائي',
      'water': 'كثير',
      'soil': 'طينية غنية',
      'temp': '20-30°م',
      'harvest': '9-12 شهر',
      'diseases': ['مرض الذبول', 'تبقع الأوراق', 'نيماتودا'],
      'fertilizers': ['سماد عضوي', 'سماد غني بالبوتاسيوم'],
      'description': 'نبات استوائي سريع النمو، حساس للرياح',
    },
    {
      'id': 9,
      'name': 'فلفل',
      'icon': Icons.local_fire_department,
      'color': Colors.red,
      'season': 'صيفي',
      'water': 'متوسط',
      'soil': 'خفيفة دافئة',
      'temp': '20-30°م',
      'harvest': '60-90 يوم',
      'diseases': ['عفن الجذور', 'فيروس موزاييك'],
      'fertilizers': ['سماد متوازن', 'سماد كالسيوم'],
      'description': 'محصول حساس للحرارة المنخفضة، يحتاج شمس مباشرة',
    },
    {
      'id': 10,
      'name': 'بصل',
      'icon': Icons.grass,
      'color': Colors.orange,
      'season': 'شتوي',
      'water': 'قليل',
      'soil': 'رملية طينية',
      'temp': '13-24°م',
      'harvest': '3-5 شهور',
      'diseases': ['عفن الرقبة', 'ذبابة البصل'],
      'fertilizers': ['سماد فوسفاتي', 'سماد بوتاسي'],
      'description': 'محصول بصلبي يحتاج تربة خفيفة وجفاف قبل الحصاد',
    },
    {
      'id': 11,
      'name': 'ثوم',
      'icon': Icons.spa,
      'color': Colors.white,
      'season': 'شتوي',
      'water': 'قليل',
      'soil': 'خفيفة جيدة الصرف',
      'temp': '10-20°م',
      'harvest': '4-6 شهور',
      'diseases': ['صدأ الأوراق', 'عفن البصيلات'],
      'fertilizers': ['سلفات البوتاسيوم', 'سماد عضوي'],
      'description': 'محصول طبي وعطري، يحتاج برودة لتنمية البصيلات',
    },
    {
      'id': 12,
      'name': 'خيار',
      'icon': Icons.water_drop,
      'color': Colors.green,
      'season': 'صيفي',
      'water': 'كثير',
      'soil': 'غنية عضوية',
      'temp': '20-30°م',
      'harvest': '50-70 يوم',
      'diseases': ['بياض زغبي', 'ذبابة الثمار'],
      'fertilizers': ['سماد نيتروجيني', 'سماد متوازن'],
      'description': 'محصول سريع النمو، يحتاج ري منتظم وحرارة',
    },
    {
      'id': 13,
      'name': 'جزر',
      'icon': Icons.grass,
      'color': Colors.orange,
      'season': 'شتوي',
      'water': 'متوسط',
      'soil': 'رملية عميقة',
      'temp': '15-20°م',
      'harvest': '2-3 شهور',
      'diseases': ['تعفن الجذور', 'ذبابة الجزر'],
      'fertilizers': ['سماد بوتاسي', 'سماد فوسفاتي'],
      'description': 'جذور وتدية تحتاج تربة عميقة خالية من الحجارة',
    },
    {
      'id': 14,
      'name': 'فراولة',
      'icon': Icons.spa,
      'color': Colors.red,
      'season': 'شتوي',
      'water': 'متوسط',
      'soil': 'حمضية خفيفة',
      'temp': '15-22°م',
      'harvest': 'مستمر',
      'diseases': ['عفن الثمار', 'ذبول الفرتسليوم'],
      'fertilizers': ['سماد عضوي', 'سماد متوازن'],
      'description': 'محصول عالي القيمة، يحتاج تربة مغذية وتهوية',
    },
    {
      'id': 15,
      'name': 'مانجو',
      'icon': Icons.forest,
      'color': Colors.orange,
      'season': 'استوائي',
      'water': 'متوسط',
      'soil': 'عميقة جيدة الصرف',
      'temp': '24-30°م',
      'harvest': 'صيفي',
      'diseases': ['العفن الفحمي', 'ذبابة الفاكهة'],
      'fertilizers': ['سماد عضوي', 'سماد NPK'],
      'description': 'شجرة استوائية كبيرة، تحتاج مساحة ووقت للنضج',
    },
    {
      'id': 16,
      'name': 'ليمون',
      'icon': Icons.spa,
      'color': Colors.yellow,
      'season': 'معتدل',
      'water': 'متوسط',
      'soil': 'جيدة الصرف',
      'temp': '15-30°م',
      'harvest': 'مستمر',
      'diseases': ['جرب الحمضيات', 'ذبابة الفاكهة'],
      'fertilizers': ['سماد حمضي', 'سماد مغنيسيوم'],
      'description': 'شجرة مثمرة دائمة الخضرة، تتحمل الجفاف نسبياً',
    },
    {
      'id': 17,
      'name': 'زيتون',
      'icon': Icons.park,
      'color': Colors.green,
      'season': 'معتدل',
      'water': 'قليل',
      'soil': 'كلسية',
      'temp': '15-25°م',
      'harvest': 'خريفي',
      'diseases': ['عين الطاووس', 'ذبابة الزيتون'],
      'fertilizers': ['سماد بوتاسي', 'سماد عضوي'],
      'description': 'شجرة معمرة مقاومة للجفاف، تحتاج شمس كاملة',
    },
    {
      'id': 18,
      'name': 'رمان',
      'icon': Icons.spa,
      'color': Colors.red,
      'season': 'معتدل',
      'water': 'قليل',
      'soil': 'جافة جيدة الصرف',
      'temp': '18-35°م',
      'harvest': 'خريفي',
      'diseases': ['تعفن الثمار', 'حفار الساق'],
      'fertilizers': ['سماد عضوي', 'سماد متوازن'],
      'description': 'شجرة متساقطة الأوراق، تتحمل الملوحة والجفاف',
    },
    {
      'id': 19,
      'name': 'باذنجان',
      'icon': Icons.spa,
      'color': Colors.purple,
      'season': 'صيفي',
      'water': 'متوسط',
      'soil': 'غنية عضوية',
      'temp': '22-30°م',
      'harvest': '70-85 يوم',
      'diseases': ['ذبول الفيوزاريوم', 'حشرة المن'],
      'fertilizers': ['سماد نيتروجيني', 'سماد فوسفاتي'],
      'description': 'محصول صيفي حساس للبرودة، يحتاج تربة دافئة',
    },
    {
      'id': 20,
      'name': 'سمسم',
      'icon': Icons.grass,
      'color': Colors.brown,
      'season': 'صيفي',
      'water': 'قليل',
      'soil': 'رملية خفيفة',
      'temp': '25-35°م',
      'harvest': '3-4 شهور',
      'diseases': ['ذبول الأوراق', 'العفن الجذري'],
      'fertilizers': ['سماد فوسفاتي', 'سماد بوتاسي'],
      'description': 'محصول زيتي مقاوم للجفاف، يحتاج حرارة عالية',
    },
  ];
  
  static List<Map<String, dynamic>> features = [
    {'icon': Icons.agriculture, 'title': 'تشخيص الأمراض', 'color': Colors.green},
    {'icon': Icons.water_drop, 'title': 'نظم الري', 'color': Colors.blue},
    {'icon': Icons.science, 'title': 'بحث علمي', 'color': Colors.purple},
    {'icon': Icons.shopping_cart, 'title': 'متجر زراعي', 'color': Colors.orange},
    {'icon': Icons.support_agent, 'title': 'استشارات', 'color': Colors.red},
    {'icon': Icons.book, 'title': 'مكتبة علمية', 'color': Colors.teal},
    {'icon': Icons.calendar_today, 'title': 'مواسم الزراعة', 'color': Colors.indigo},
    {'icon': Icons.analytics, 'title': 'تحليل التربة', 'color': Colors.brown},
  ];
  
  static List<Map<String, dynamic>> products = [
    {'name': 'بذور قمح', 'price': '25 ريال', 'icon': Icons.grass, 'category': 'بذور'},
    {'name': 'سماد عضوي', 'price': '80 ريال', 'icon': Icons.eco, 'category': 'أسمدة'},
    {'name': 'مبيد فطري', 'price': '45 ريال', 'icon': Icons.medical_services, 'category': 'مبيدات'},
    {'name': 'أدوات زراعة', 'price': '150 ريال', 'icon': Icons.build, 'category': 'أدوات'},
    {'name': 'رشاش مائي', 'price': '200 ريال', 'icon': Icons.water_drop, 'category': 'ري'},
    {'name': 'تربة زراعية', 'price': '60 ريال', 'icon': Icons.landscape, 'category': 'تربة'},
    {'name': 'صوبة زراعة', 'price': '500 ريال', 'icon': Icons.home, 'category': 'معدات'},
    {'name': 'بذور خضروات', 'price': '30 ريال', 'icon': Icons.spa, 'category': 'بذور'},
  ];
}

// ==================== الشاشة الرئيسية ====================
class MainHomeScreen extends StatefulWidget {
  @override
  _MainHomeScreenState createState() => _MainHomeScreenState();
}

class _MainHomeScreenState extends State<MainHomeScreen> {
  int _selectedIndex = 0;
  
  final List<Widget> _screens = [
    HomeScreen(),
    CropsScreen(),
    ScienceScreen(),
    ConsultationScreen(),
    MarketScreen(),
  ];
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: _selectedIndex == 0 ? _buildAppBar() : null,
      body: _screens[_selectedIndex],
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _selectedIndex,
        onTap: (index) => setState(() => _selectedIndex = index),
        type: BottomNavigationBarType.fixed,
        selectedItemColor: Colors.green[700],
        unselectedItemColor: Colors.grey[600],
        items: [
          BottomNavigationBarItem(icon: Icon(Icons.home), label: 'الرئيسية'),
          BottomNavigationBarItem(icon: Icon(Icons.agriculture), label: 'المحاصيل'),
          BottomNavigationBarItem(icon: Icon(Icons.science), label: 'بحث علمي'),
          BottomNavigationBarItem(icon: Icon(Icons.phone), label: 'استشارات'),
          BottomNavigationBarItem(icon: Icon(Icons.shop), label: 'المتجر'),
        ],
      ),
    );
  }
  
  AppBar _buildAppBar() {
    return AppBar(
      title: Row(
        children: [
          Icon(Icons.agriculture, color: Colors.white),
          SizedBox(width: 10),
          Text('المرشد الزراعي المتكامل'),
        ],
      ),
      backgroundColor: Colors.green[700],
      elevation: 4,
      actions: [
        IconButton(
          icon: Icon(Icons.share),
          onPressed: _shareApp,
        ),
        IconButton(
          icon: Icon(Icons.search),
          onPressed: () {},
        ),
      ],
    );
  }
  
  void _shareApp() {
    Share.share(
      '🌱 المرشد الزراعي المتكامل\n'
      'تطبيق شامل لـ 20 محصول زراعي\n'
      'استشارات مجانية: ${AppData.supportWhatsApp}\n'
      'البريد: ${AppData.supportEmail}\n'
      'حمله الآن!',
      subject: 'المرشد الزراعي المتكامل',
    );
  }
}

// ==================== شاشة الرئيسية ====================
class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SingleChildScrollView(
      padding: EdgeInsets.all(16),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Card(
            elevation: 4,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(20),
            ),
            child: Container(
              decoration: BoxDecoration(
                gradient: LinearGradient(
                  colors: [Colors.green[400]!, Colors.lightGreen[700]!],
                  begin: Alignment.topLeft,
                  end: Alignment.bottomRight,
                ),
                borderRadius: BorderRadius.circular(20),
              ),
              padding: EdgeInsets.all(25),
              child: Column(
                children: [
                  Row(
                    children: [
                      Icon(Icons.agriculture, size: 60, color: Colors.white),
                      SizedBox(width: 15),
                      Expanded(
                        child: Column(
                          crossAxisAlignment: CrossAxisAlignment.start,
                          children: [
                            Text('مرحباً بك',
                              style: TextStyle(
                                fontSize: 24,
                                fontWeight: FontWeight.bold,
                                color: Colors.white,
                              ),
                            ),
                            Text('في مكتبتك الزراعية الشاملة',
                              style: TextStyle(fontSize: 16, color: Colors.white70),
                            ),
                          ],
                        ),
                      ),
                    ],
                  ),
                  SizedBox(height: 15),
                  Text('تطبيق متكامل لـ 20 محصول مع معلومات مفصلة عن كل محصول',
                    style: TextStyle(fontSize: 14, color: Colors.white),
                    textAlign: TextAlign.center,
                  ),
                ],
              ),
            ),
          ),
          
          SizedBox(height: 25),
          
          Card(
            child: Padding(
              padding: EdgeInsets.all(15),
              child: Row(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: [
                  _statCard('20', 'محصول', Colors.green, Icons.agriculture),
                  _statCard('24/7', 'دعم', Colors.blue, Icons.support_agent),
                  _statCard('50+', 'منتج', Colors.orange, Icons.shopping_cart),
                  _statCard('100%', 'مجاني', Colors.purple, Icons.verified),
                ],
              ),
            ),
          ),
          
          SizedBox(height: 25),
          
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceBetween,
            children: [
              Text('خدمات التطبيق',
                style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold, color: Colors.green[800]),
              ),
              Chip(
                label: Text('${AppData.features.length} خدمة'),
                backgroundColor: Colors.green[100],
              ),
            ],
          ),
          SizedBox(height: 15),
          
          GridView.builder(
            shrinkWrap: true,
            physics: NeverScrollableScrollPhysics(),
            gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
              crossAxisCount: 4,
              childAspectRatio: 1,
              crossAxisSpacing: 8,
              mainAxisSpacing: 8,
            ),
            itemCount: AppData.features.length,
            itemBuilder: (context, index) {
              return _featureCard(AppData.features[index]);
            },
          ),
          
          SizedBox(height: 25),
          
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceBetween,
            children: [
              Text('أهم المحاصيل',
                style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold, color: Colors.green[800]),
              ),
              TextButton.icon(
                onPressed: () {},
                icon: Icon(Icons.arrow_back_ios, size: 14),
                label: Text('عرض الكل'),
              ),
            ],
          ),
          SizedBox(height: 15),
          
          Container(
            height: 150,
            child: ListView.builder(
              scrollDirection: Axis.horizontal,
              itemCount: AppData.crops.length,
              itemBuilder: (context, index) {
                return _cropPreview(AppData.crops[index], context);
              },
            ),
          ),
          
          SizedBox(height: 25),
          
          Card(
            color: Colors.orange[50],
            child: Padding(
              padding: EdgeInsets.all(16),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Row(
                    children: [
                      Icon(Icons.calendar_today, color: Colors.orange),
                      SizedBox(width: 10),
                      Text('محاصيل هذا الموسم',
                        style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
                      ),
                    ],
                  ),
                  SizedBox(height: 10),
                  Text('شتوي: قمح، بطاطس، ثوم، جزر، فراولة',
                    style: TextStyle(fontSize: 14),
                  ),
                  Text('صيفي: ذرة، طماطم، فلفل، خيار، سمسم',
                    style: TextStyle(fontSize: 14),
                  ),
                ],
              ),
            ),
          ),
          
          SizedBox(height: 25),
          
          Row(
            children: [
              Expanded(
                child: Card(
                  color: Colors.green[50],
                  child: ListTile(
                    leading: Icon(Icons.phone, color: Colors.green),
                    title: Text('استشارة فورية'),
                    subtitle: Text('واتساب دعم فني'),
                    trailing: Icon(Icons.arrow_forward),
                    onTap: () => _launchWhatsApp(context),
                  ),
                ),
              ),
              SizedBox(width: 10),
              Expanded(
                child: Card(
                  color: Colors.blue[50],
                  child: ListTile(
                    leading: Icon(Icons.email, color: Colors.blue),
                    title: Text('بريد إلكتروني'),
                    subtitle: Text('إرسال استفسار'),
                    trailing: Icon(Icons.arrow_forward),
                    onTap: () => _launchEmail(context),
                  ),
                ),
              ),
            ],
          ),
          
          SizedBox(height: 20),
        ],
      ),
    );
  }
  
  Widget _statCard(String value, String label, Color color, IconData icon) {
    return Column(
      children: [
        Container(
          padding: EdgeInsets.all(12),
          decoration: BoxDecoration(
            color: color.withOpacity(0.1),
            shape: BoxShape.circle,
          ),
          child: Icon(icon, color: color, size: 20),
        ),
        SizedBox(height: 8),
        Text(value,
          style: TextStyle(
            fontSize: 16,
            fontWeight: FontWeight.bold,
            color: color,
          ),
        ),
        Text(label,
          style: TextStyle(fontSize: 12, color: Colors.grey),
        ),
      ],
    );
  }
  
  Widget _featureCard(Map<String, dynamic> feature) {
    return Card(
      elevation: 2,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(12),
      ),
      child: Container(
        decoration: BoxDecoration(
          borderRadius: BorderRadius.circular(12),
          border: Border.all(color: feature['color'].withOpacity(0.3), width: 1),
        ),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(feature['icon'], size: 24, color: feature['color']),
            SizedBox(height: 8),
            Text(feature['title'],
              style: TextStyle(fontSize: 10, fontWeight: FontWeight.bold),
              textAlign: TextAlign.center,
              maxLines: 2,
            ),
          ],
        ),
      ),
    );
  }
  
  Widget _cropPreview(Map<String, dynamic> crop, BuildContext context) {
    return Container(
      width: 120,
      margin: EdgeInsets.only(right: 10),
      child: Card(
        shape: RoundedRectangleBorder(
          borderRadius: BorderRadius.circular(12),
        ),
        child: InkWell(
          borderRadius: BorderRadius.circular(12),
          onTap: () => _showCropDetails(crop, context),
          child: Padding(
            padding: EdgeInsets.all(12),
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Container(
                  padding: EdgeInsets.all(8),
                  decoration: BoxDecoration(
                    color: crop['color'].withOpacity(0.1),
                    shape: BoxShape.circle,
                  ),
                  child: Icon(crop['icon'], size: 24, color: crop['color']),
                ),
                SizedBox(height: 10),
                Text(crop['name'],
                  style: TextStyle(fontSize: 14, fontWeight: FontWeight.bold),
                  textAlign: TextAlign.center,
                  maxLines: 2,
                ),
                SizedBox(height: 5),
                Chip(
                  label: Text(crop['season'],
                    style: TextStyle(fontSize: 10),
                  ),
                  backgroundColor: crop['color'].withOpacity(0.1),
                  padding: EdgeInsets.symmetric(horizontal: 4),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
  
  void _showCropDetails(Map<String, dynamic> crop, BuildContext context) {
    showModalBottomSheet(
      context: context,
      isScrollControlled: true,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.vertical(top: Radius.circular(25)),
      ),
      builder: (context) {
        return CropDetailsSheet(crop: crop);
      },
    );
  }
  
  void _launchWhatsApp(BuildContext context) async {
    final url = 'https://wa.me/${AppData.supportWhatsApp}?text=مرحباً، أريد استشارة زراعية حول المحاصيل';
    if (await canLaunch(url)) {
      await launch(url);
    } else {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('تعذر فتح واتساب')),
      );
    }
  }
  
  void _launchEmail(BuildContext context) async {
    final url = 'mailto:${AppData.supportEmail}?subject=استشارة زراعية&body=مرحباً، أريد معرفة معلومات عن...';
    if (await canLaunch(url)) {
      await launch(url);
    } else {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('تعذر فتح البريد')),
      );
    }
  }
}

// ==================== شاشة تفاصيل المحصول ====================
class CropDetailsSheet extends StatelessWidget {
  final Map<String, dynamic> crop;
  
  CropDetailsSheet({required this.crop});
  
  @override
  Widget build(BuildContext context) {
    return Container(
      padding: EdgeInsets.all(20),
      decoration: BoxDecoration(
        borderRadius: BorderRadius.vertical(top: Radius.circular(25)),
        color: Colors.white,
      ),
      child: SingleChildScrollView(
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          mainAxisSize: MainAxisSize.min,
          children: [
            Center(
              child: Container(
                width: 60,
                height: 5,
                decoration: BoxDecoration(
                  color: Colors.grey[300],
                  borderRadius: BorderRadius.circular(5),
                ),
              ),
            ),
            SizedBox(height: 20),
            
            Row(
              children: [
                Container(
                  padding: EdgeInsets.all(12),
                  decoration: BoxDecoration(
                    color: crop['color'].withOpacity(0.1),
                    shape: BoxShape.circle,
                  ),
                  child: Icon(crop['icon'], size: 30, color: crop['color']),
                ),
                SizedBox(width: 15),
                Expanded(
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      Text(crop['name'],
                        style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
                      ),
                      Text(crop['season'],
                        style: TextStyle(fontSize: 16, color: Colors.grey),
                      ),
                    ],
                  ),
                ),
                IconButton(
                  icon: Icon(Icons.share),
                  onPressed: () => _shareCrop(context),
                ),
              ],
            ),
            
            SizedBox(height: 20),
            
            Text(crop['description'],
              style: TextStyle(fontSize: 16, height: 1.5),
              textAlign: TextAlign.justify,
            ),
            
            SizedBox(height: 25),
            
            Text('المعلومات الفنية',
              style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold, color: Colors.green[800]),
            ),
            SizedBox(height: 10),
            
            GridView.count(
              shrinkWrap: true,
              physics: NeverScrollableScrollPhysics(),
              crossAxisCount: 2,
              childAspectRatio: 3,
              crossAxisSpacing: 10,
              mainAxisSpacing: 10,
              children: [
                _infoCard('الموسم', crop['season'], Icons.calendar_today),
                _infoCard('مياه الري', crop['water'], Icons.water_drop),
                _infoCard('درجة الحرارة', crop['temp'], Icons.thermostat),
                _infoCard('فترة الحصاد', crop['harvest'], Icons.timelapse),
              ],
            ),
            
            SizedBox(height: 25),
            
            Text('نوع التربة المفضلة',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
            ),
            SizedBox(height: 5),
            Chip(
              label: Text(crop['soil']),
              backgroundColor: Colors.brown[50],
            ),
            
            SizedBox(height: 25),
            
            Text('الأمراض الشائعة',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold, color: Colors.red[800]),
            ),
            SizedBox(height: 10),
            Wrap(
              spacing: 8,
              runSpacing: 8,
              children: (crop['diseases'] as List).map((disease) {
                return Chip(
                  label: Text(disease),
                  backgroundColor: Colors.red[50],
                  labelStyle: TextStyle(color: Colors.red[800]),
                );
              }).toList(),
            ),
            
            SizedBox(height: 25),
            
            Text('الأسمدة المقترحة',
              style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold, color: Colors.orange[800]),
            ),
            SizedBox(height: 10),
            Wrap(
              spacing: 8,
              runSpacing: 8,
              children: (crop['fertilizers'] as List).map((fertilizer) {
                return Chip(
                  label: Text(fertilizer),
                  backgroundColor: Colors.orange[50],
                  labelStyle: TextStyle(color: Colors.orange[800]),
                );
              }).toList(),
            ),
            
            SizedBox(height: 30),
            
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                ElevatedButton.icon(
                  onPressed: () => _launchWhatsAppConsult(context),
                  icon: Icon(Icons.question_answer),
                  label: Text('استشارة عن ${crop['name']}'),
                  style: ElevatedButton.styleFrom(
                    backgroundColor: Colors.green,
                    padding: EdgeInsets.symmetric(horizontal: 20, vertical: 12),
                  ),
                ),
                OutlinedButton.icon(
                  onPressed: () => Navigator.pop(context),
                  icon: Icon(Icons.close),
                  label: Text('إغلاق'),
                  style: OutlinedButton.styleFrom(
                    padding: EdgeInsets.symmetric(horizontal: 20, vertical: 12),
                  ),
                ),
              ],
            ),
            
            SizedBox(height: 20),
          ],
        ),
      ),
    );
  }
  
  Widget _infoCard(String title, String value, IconData icon) {
    return Card(
      child: ListTile(
        leading: Icon(icon, color: Colors.green),
        title: Text(title, style: TextStyle(fontSize: 12)),
        subtitle: Text(value, style: TextStyle(fontSize: 14, fontWeight: FontWeight.bold)),
        dense: true,
      ),
    );
  }
  
  void _shareCrop(BuildContext context) {
    Share.share(
      '🌱 معلومات عن ${crop['name']}\n'
      'الموسم: ${crop['season']}\n'
      'مياه الري: ${crop['water']}\n'
      'التربة: ${crop['soil']}\n'
      'الحرارة: ${crop['temp']}\n'
      'الحصاد: ${crop['harvest']}\n'
      'الأمراض: ${crop['diseases'].join('، ')}\n'
      'الأسمدة: ${crop['fertilizers'].join('، ')}\n\n'
      'مشاركة من تطبيق المرشد الزراعي المتكامل',
    );
  }
  
  void _launchWhatsAppConsult(BuildContext context) async {
    final url = 'https://wa.me/${AppData.supportWhatsApp}?text=أريد استشارة عن محصول ${crop['name']}';
    if (await canLaunch(url)) {
      await launch(url);
    } else {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('تعذر فتح واتساب')),
      );
    }
  }
}

// ==================== شاشة المحاصيل ====================
class CropsScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Padding(
          padding: EdgeInsets.all(16),
          child: Card(
            child: Padding(
              padding: EdgeInsets.all(12),
              child: Row(
                children: [
                  Icon(Icons.search, color: Colors.green),
                  SizedBox(width: 10),
                  Expanded(
                    child: TextField(
                      decoration: InputDecoration(
                        hintText: 'ابحث عن محصول...',
                        border: InputBorder.none,
                      ),
                    ),
                  ),
                  Chip(
                    label: Text('${AppData.crops.length} محصول'),
                  ),
                ],
              ),
            ),
          ),
        ),
        
        Expanded(
          child: ListView.builder(
            padding: EdgeInsets.symmetric(horizontal: 16),
            itemCount: AppData.crops.length,
            itemBuilder: (context, index) {
              return _cropCard(AppData.crops[index], context);
            },
          ),
        ),
      ],
    );
  }
  
  Widget _cropCard(Map<String, dynamic> crop, BuildContext context) {
    return Card(
      margin: EdgeInsets.only(bottom: 12),
      child: ListTile(
        leading: CircleAvatar(
          backgroundColor: crop['color'].withOpacity(0.1),
          child: Icon(crop['icon'], color: crop['color']),
        ),
        title: Text(crop['name'],
          style: TextStyle(fontWeight: FontWeight.bold),
        ),
        subtitle: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Row(
              children: [
                Icon(Icons.calendar_today, size: 14),
                SizedBox(width: 5),
                Text(crop['season']),
              ],
            ),
            Row(
              children: [
                Icon(Icons.water_drop, size: 14),
                SizedBox(width: 5),
                Text('ري: ${crop['water']}'),
              ],
            ),
          ],
        ),
        trailing: Icon(Icons.arrow_forward_ios, size: 16),
        onTap: () => _showCropDetails(crop, context),
      ),
    );
  }
  
  void _showCropDetails(Map<String, dynamic> crop, BuildContext context) {
    showModalBottomSheet(
      context: context,
      isScrollControlled: true,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.vertical(top: Radius.circular(25)),
      ),
      builder: (context) {
        return CropDetailsSheet(crop: crop);
      },
    );
  }
}

// ==================== شاشة البحث العلمي ====================
class ScienceScreen extends StatelessWidget {
  final List<Map<String, dynamic>> articles = [
    {
      'title': 'التسميد المتوازن',
      'content': 'كيفية تحقيق التوازن بين العناصر الغذائية في التربة',
      'icon': Icons.eco,
      'category': 'أسمدة',
    },
    {
      'title': 'مقاومة الآفات',
      'content': 'طرق المكافحة المتكاملة للآفات الزراعية',
      'icon': Icons.bug_report,
      'category': 'وقاية',
    },
    {
      'title': 'الري بالتنقيط',
      'content': 'تقنيات الري الحديثة وتوفير المياه',
      'icon': Icons.water_drop,
      'category': 'ري',
    },
    {
      'title': 'الزراعة العضوية',
      'content': 'مبادئ الزراعة المستدامة والخالية من الكيماويات',
      'icon': Icons.agriculture,
      'category': 'عضوي',
    },
    {
      'title': 'دراسة عن القات',
      'content': 'أبحاث علمية عن نبات القات (Catha edulis)',
      'icon': Icons.forest,
      'category': 'نباتات',
    },
    {
      'title': 'تسميد أشجار الفاكهة',
      'content': 'برامج التسميد المثلى لأشجار الفاكهة',
      'icon': Icons.park,
      'category': 'أشجار',
    },
  ];
  
  @override
  Widget build(BuildContext context) {
    return ListView(
      padding: EdgeInsets.all(16),
      children: [
        Card(
          child: Padding(
            padding: EdgeInsets.all(20),
            child: Column(
              children: [
                Icon(Icons.science, size: 60, color: Colors.purple),
                SizedBox(height: 15),
                Text('المكتبة العلمية الزراعية',
                  style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
                ),
                SizedBox(height: 10),
                Text('أبحاث ودراسات متخصصة في المجال الزراعي',
                  style: TextStyle(fontSize: 16, color: Colors.grey),
                  textAlign: TextAlign.center,
                ),
              ],
            ),
          ),
        ),
        
        SizedBox(height: 20),
        
        ...articles.map((article) {
          return Card(
            margin: EdgeInsets.only(bottom: 10),
            child: ListTile(
              leading: Container(
                padding: EdgeInsets.all(8),
                decoration: BoxDecoration(
                  color: Colors.purple.withOpacity(0.1),
                  shape: BoxShape.circle,
                ),
                child: Icon(article['icon'], color: Colors.purple),
              ),
              title: Text(article['title'],
                style: TextStyle(fontWeight: FontWeight.bold),
              ),
              subtitle: Text(article['content']),
              trailing: Chip(
                label: Text(article['category']),
                backgroundColor: Colors.purple[50],
              ),
              onTap: () => _showArticle(article, context),
            ),
          );
        }).toList(),
      ],
    );
  }
  
  void _showArticle(Map<String, dynamic> article, BuildContext context) {
    showDialog(
      context: context,
      builder: (context) => AlertDialog(
        title: Text(article['title']),
        content: SingleChildScrollView(
          child: Text(article['content']),
        ),
        actions: [
          TextButton(
            onPressed: () => Navigator.pop(context),
            child: Text('إغلاق'),
          ),
          TextButton(
            onPressed: () {
              Navigator.pop(context);
              Share.share('مقالة زراعية: ${article['title']}\n${article['content']}\n\nمن تطبيق المرشد الزراعي');
            },
            child: Text('مشاركة'),
          ),
        ],
      ),
    );
  }
}

// ==================== شاشة الاستشارات ====================
class ConsultationScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SingleChildScrollView(
      padding: EdgeInsets.all(16),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          Card(
            elevation: 5,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(20),
            ),
            child: Padding(
              padding: EdgeInsets.all(20),
              child: Column(
                children: [
                  Icon(Icons.support_agent, size: 70, color: Colors.red),
                  SizedBox(height: 15),
                  Text('مركز الاستشارات الزراعية',
                    style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
                  ),
                  SizedBox(height: 10),
                  Text('فريق من المهندسين الزراعيين على مدار الساعة',
                    style: TextStyle(fontSize: 16, color: Colors.grey),
                  ),
                ],
              ),
            ),
          ),
          
          SizedBox(height: 25),
          
          Text('تواصل مباشر',
            style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
          ),
          SizedBox(height: 15),
          
          GridView.count(
            shrinkWrap: true,
            physics: NeverScrollableScrollPhysics(),
            crossAxisCount: 2,
            childAspectRatio: 1.5,
            crossAxisSpacing: 10,
            mainAxisSpacing: 10,
            children: [
              _contactCard(Icons.whatsapp, 'واتساب', Colors.green, () => _launchWhatsApp(context)),
              _contactCard(Icons.email, 'بريد', Colors.red, () => _launchEmail(context)),
              _contactCard(Icons.phone, 'اتصال', Colors.blue, () => _launchPhone(context)),
              _contactCard(Icons.video_call, 'مكالمة', Colors.purple, () => _launchWhatsApp(context)),
            ],
          ),
          
          SizedBox(height: 25),
        ],
      ),
    );
  }
  
  Widget _contactCard(IconData icon, String title, Color color, Function onTap) {
    return Card(
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(15),
      ),
      child: InkWell(
        borderRadius: BorderRadius.circular(15),
        onTap: () => onTap(),
        child: Container(
          padding: EdgeInsets.all(20),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Icon(icon, size: 40, color: color),
              SizedBox(height: 15),
              Text(title,
                style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
              ),
            ],
          ),
        ),
      ),
    );
  }
  
  void _launchWhatsApp(BuildContext context) async {
    final url = 'https://wa.me/${AppData.supportWhatsApp}?text=مرحباً، أريد استشارة زراعية';
    if (await canLaunch(url)) {
      await launch(url);
    } else {
      _showError(context, 'تعذر فتح واتساب');
    }
  }
  
  void _launchEmail(BuildContext context) async {
    final url = 'mailto:${AppData.supportEmail}?subject=استشارة زراعية';
    if (await canLaunch(url)) {
      await launch(url);
    } else {
      _showError(context, 'تعذر فتح البريد');
    }
  }
  
  void _launchPhone(BuildContext context) async {
    final url = 'tel:${AppData.supportWhatsApp}';
    if (await canLaunch(url)) {
      await launch(url);
    } else {
      _showError(context, 'تعذر فتح الهاتف');
    }
  }
  
  void _showError(BuildContext context, String message) {
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(content: Text(message)),
    );
  }
}

// ==================== شاشة المتجر ====================
class MarketScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Padding(
          padding: EdgeInsets.all(16),
          child: Card(
            child: Padding(
              padding: EdgeInsets.all(16),
              child: Row(
                children: [
                  Icon(Icons.store, color: Colors.orange, size: 40),
                  SizedBox(width: 15),
                  Expanded(
                    child: Column(
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text('المتجر الزراعي الشامل',
                          style: TextStyle(fontSize: 22, fontWeight: FontWeight.bold),
                        ),
                        Text('أدوات، أسمدة، مبيدات، بذور',
                          style: TextStyle(color: Colors.grey),
                        ),
                      ],
                    ),
                  ),
                  Chip(
                    label: Text('${AppData.products.length} منتج'),
                    backgroundColor: Colors.orange[100],
                  ),
                ],
              ),
            ),
          ),
        ),
        
        Expanded(
          child: GridView.builder(
            padding: EdgeInsets.all(16),
            gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
              crossAxisCount: 2,
              crossAxisSpacing: 15,
              mainAxisSpacing: 15,
              childAspectRatio: 0.85,
            ),
            itemCount: AppData.products.length,
            itemBuilder: (context, index) {
              return _productCard(AppData.products[index], context);
            },
          ),
        ),
      ],
    );
  }
  
  Widget _productCard(Map<String, dynamic> product, BuildContext context) {
    return Card(
      elevation: 3,
      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(15),
      ),
      child: Column(
        children: [
          Container(
            height: 120,
            decoration: BoxDecoration(
              color: Colors.grey[100],
              borderRadius: BorderRadius.vertical(top: Radius.circular(15)),
            ),
            child: Center(
              child: Icon(product['icon'], size: 60, color: Colors.green),
            ),
          ),
          Padding(
            padding: EdgeInsets.all(12),
            child: Column(
              children: [
                Text(product['name'],
                  style: TextStyle(fontSize: 16, fontWeight: FontWeight.bold),
                  textAlign: TextAlign.center,
                  maxLines: 2,
                ),
                SizedBox(height: 8),
                Chip(
                  label: Text(product['category']),
                  backgroundColor: Colors.green[50],
                  labelStyle: TextStyle(fontSize: 10),
                ),
                SizedBox(height: 8),
                Text(product['price'],
                  style: TextStyle(fontSize: 18, color: Colors.green[800], fontWeight: FontWeight.bold),
                ),
                SizedBox(height: 10),
                ElevatedButton.icon(
                  onPressed: () => _orderProduct(product, context),
                  icon: Icon(Icons.shopping_cart, size: 16),
                  label: Text('شراء'),
                  style: ElevatedButton.styleFrom(
                    minimumSize: Size(double.infinity, 40),
                  ),
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }
  
  void _orderProduct(Map<String, dynamic> product, BuildContext context) {
    showDialog(
      context: context,
      builder: (context) => AlertDialog(
        title: Text('طلب ${product['name']}'),
        content: Text('سعر المنتج: ${product['price']}\n\nسيتم التواصل معك على واتساب لتأكيد الطلب والتفاصيل'),
        actions: [
          TextButton(
            onPressed: () => Navigator.pop(context),
            child: Text('إلغاء'),
          ),
          ElevatedButton(
            onPressed: () {
              Navigator.pop(context);
              _launchWhatsAppOrder(product, context);
            },
            child: Text('تأكيد الطلب'),
          ),
        ],
      ),
    );
  }
  
  void _launchWhatsAppOrder(Map<String, dynamic> product, BuildContext context) async {
    final url = 'https://wa.me/${AppData.supportWhatsApp}?text=أريد طلب ${product['name']} - ${product['price']} - فئة: ${product['category']}';
    
    try {
      if (await canLaunch(url)) {
        await launch(url);
        ScaffoldMessenger.of(context).showSnackBar(
          SnackBar(
            content: Text('تم فتح واتساب لإكمال الطلب'),
            duration: Duration(seconds: 2),
          ),
        );
      } else {
        ScaffoldMessenger.of(context).showSnackBar(
          SnackBar(
            content: Text('تعذر فتح واتساب'),
          ),
        );
      }
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(
          content: Text('حدث خطأ: $e'),
        ),
      );
    }
  }
}