# HealthBridge - NAMASTE + ICD EMR System

A comprehensive Electronic Medical Records (EMR) system that bridges traditional AYUSH medicine (NAMASTE codes) with international standards (ICD-11), featuring FHIR R4 interoperability and modern web interface.

## Features

### Core Functionality
- **Multi-User Authentication**: Role-based access (Admin, Doctor, Patient) with Google OAuth2 support
- **Patient Management**: Complete patient records with ABHA ID integration
- **Medical Code Search**: Unified search across NAMASTE (AYUSH) and ICD-11 code systems
- **Diagnosis Management**: Save and track patient diagnoses with code mapping
- **FHIR R4 Compliance**: Full FHIR bundle upload, validation, and export capabilities
- **Analytics & Reports**: Comprehensive reporting with PDF/Excel export
- **Patient History**: Timeline view of medical records with FHIR export

### Technical Features
- **Modern UI**: Responsive design with futuristic dashboard themes
- **API Integration**: WHO ICD-11 API integration for real-time code lookup
- **Database Support**: SQLite databases for patient data, diagnoses, and FHIR bundles
- **Security**: JWT authentication for API access, secure session management
- **Interoperability**: FHIR R4 CodeSystem, ValueSet, and ConceptMap support

## Quick Start

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Run the Application
```bash
python app.py
```
Access the application at: http://localhost:8000

### 3. Default Login
- Create a new account via the signup page
- All new accounts are created with Doctor role by default

## Project Structure

### Core Application Files
- `app.py` - Main Flask application with API routes
- `enhanced_routes.py` - Authentication and user management
- `patient_routes.py` - Patient management functionality
- `fhir_routes.py` - FHIR interoperability features
- `reports_routes.py` - Analytics and reporting

### Database Models
- `enhanced_auth.py` - User authentication and roles
- `patient_models.py` - Patient data management
- `database.py` - Core database operations

### Services
- `csv_service.py` - NAMASTE codes management
- `fhir_service.py` - FHIR resource creation
- `icd11_api.py` - WHO ICD-11 API integration
- `analytics_engine.py` - Data analytics and reporting
- `abha_validator.py` - ABHA ID validation

### Templates
- `templates/enhanced_auth/` - Login, signup, and dashboards
- `templates/patients/` - Patient management interfaces
- `templates/fhir/` - FHIR bundle management
- `templates/reports/` - Analytics dashboards
- `templates/` - Core pages (search, diagnosis, history)

## API Endpoints

### Authentication
- `POST /enhanced/login` - User login
- `POST /enhanced/signup` - User registration
- `GET /enhanced/logout` - User logout

### Medical Code Search
- `GET /search?q=<query>` - Unified NAMASTE + ICD-11 search
- `GET /icd11/search?q=<query>` - ICD-11 only search
- `GET /conceptmap/translate?code=<code>` - NAMASTE to ICD-11 translation

### Patient Management
- `GET /patients/` - Patient list interface
- `POST /patients/add` - Add new patient
- `GET /patients/<id>` - Patient details
- `POST /patients/<id>/diagnosis` - Add diagnosis

### FHIR Interoperability
- `POST /fhir/upload` - Upload FHIR bundle
- `GET /patients/<id>/fhir` - Get patient as FHIR resource
- `GET /patient/<id>/history?format=fhir` - Patient history as FHIR bundle

### Diagnosis & History
- `POST /diagnosis` - Save patient diagnosis
- `GET /patient/<id>/history` - Get patient medical history

## Configuration

### ICD-11 API Setup
Update the WHO credentials in `app.py`:
```python
configure_icd_api(
    client_id='your-client-id',
    client_secret='your-client-secret'
)
```

### Google OAuth2 Setup
Update credentials in `enhanced_routes.py`:
```python
GOOGLE_CLIENT_ID = 'your-google-client-id'
GOOGLE_CLIENT_SECRET = 'your-google-client-secret'
```

## Database Files
- `enhanced_auth.db` - User accounts and authentication
- `patients.db` - Patient records and diagnoses
- `fhir_bundles.db` - FHIR bundle storage
- `diagnosis.db` - Legacy diagnosis records
- `icd_cache.db` - ICD-11 API response cache

## Key Features in Detail

### 1. Medical Code Integration
- **NAMASTE Codes**: Local CSV-based AYUSH medical codes
- **ICD-11 Integration**: Real-time WHO API integration
- **Code Translation**: Automated mapping between systems
- **FHIR Compliance**: Standard-compliant CodeSystem and ValueSet resources

### 2. Patient Management
- **ABHA ID Support**: Indian healthcare ID validation and formatting
- **Comprehensive Records**: Demographics, medical history, allergies
- **Diagnosis Tracking**: Timeline-based diagnosis management
- **FHIR Export**: Patient data as FHIR Patient resources

### 3. FHIR R4 Interoperability
- **Bundle Validation**: Comprehensive FHIR bundle structure validation
- **Resource Creation**: Automatic FHIR resource generation
- **Standard Compliance**: Full FHIR R4 specification adherence
- **Export Capabilities**: JSON download of FHIR resources

### 4. Analytics & Reporting
- **Dashboard Analytics**: Real-time statistics and charts
- **Export Options**: PDF and Excel report generation
- **Data Visualization**: Interactive charts and graphs
- **Pandas Integration**: Advanced data processing and analysis

## Security Features
- **Role-Based Access**: Admin, Doctor, Patient role separation
- **Session Management**: Secure Flask-Login integration
- **JWT Authentication**: API access token system
- **Input Validation**: Comprehensive data validation and sanitization
- **ABHA ID Validation**: Secure healthcare ID processing

## Browser Compatibility
- Modern browsers with ES6+ support
- Responsive design for mobile and desktop
- Progressive Web App features

## Contributing
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License
This project is developed for healthcare interoperability and AYUSH-modern medicine integration.

## Support
For technical support or feature requests, please refer to the project documentation or contact the development team.