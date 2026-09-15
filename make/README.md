# Make Blueprint

התיקייה הזאת מכילה את ה־Blueprint הציבורי של Make.com עבור פרויקט תיבת התפעול החכמה.

ה־Blueprint שנשמר ב־Repository עבר Sanitization בכוונה לפני פרסום ציבורי. הוא לא אמור לכלול API Keys אמיתיים, Bot Tokens, כתובות Webhook, מזהי Chat פרטיים, מזהי Spreadsheet, פרטי OAuth או מזהי חיבור אישיים.

## הערות לייבוא

לאחר ייבוא ה־Blueprint לתוך Make, יש להגדיר את החיבורים האישיים שלך עבור:

- Custom Webhook
- חיבור OpenAI
- Make Data Store
- חיבור Telegram Bot ו־Chat ID
- חיבור Gmail
- חיבור Google Sheets וה־Spreadsheet המתאים

ה־Repository כולל גם נתוני הזמנות סינתטיים לדוגמה בקובץ `sample-data/orders.csv`, כך שניתן לשחזר את לוגיקת החיפוש בלי לחשוף Spreadsheet פרטי.

ה־Blueprint אינו צפוי לפעול מיד לאחר הייבוא עד שהחיבורים הספציפיים לסביבה יוגדרו.