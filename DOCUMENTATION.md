# Alok AI Mock Interview - Project Documentation

## 📋 Table of Contents
1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Technology Stack](#technology-stack)
4. [System Architecture](#system-architecture)
5. [Installation & Setup](#installation--setup)
6. [Project Structure](#project-structure)
7. [Core Components](#core-components)
8. [Database Schema](#database-schema)
9. [API Endpoints](#api-endpoints)
10. [Future Enhancements](#future-enhancements)

---

## 🎯 Project Overview

**Alok AI Mock Interview** is an intelligent mock interview preparation platform that helps candidates practice and improve their interview skills through AI-powered conversations. The application provides both text-based and voice-based interview modes with real-time feedback.

### Problem Statement
Job seekers often lack access to quality interview practice opportunities. Traditional mock interviews require scheduling with mentors or peers, making it difficult to practice on-demand.

### Solution
An AI-powered interview coach that:
- Provides 24/7 availability for practice sessions
- Offers personalized feedback on responses
- Supports multiple interview formats (text & voice)
- Tracks progress over time

---

## ✨ Features

### 1. Role-Based Interview Selection
- Software Engineer
- Product Manager  
- Data Analyst
- UX Designer
- Marketing Manager
- Sales Representative

### 2. Dual Interview Modes
| Mode | Description |
|------|-------------|
| **Text Interview** | Chat-based Q&A with real-time AI responses |
| **Live Interview** | Voice-powered conversation with speech-to-text and text-to-speech |

### 3. 3D AI Avatar
- Interactive 3D avatar using Three.js
- Visual feedback during speaking/listening states
- Animated particle effects and glow

### 4. User Authentication
- Email/password authentication
- Secure session management
- Protected routes for logged-in users

### 5. Interview History
- Save and review past interview sessions
- Track duration and performance
- Access complete conversation transcripts

---

## 🛠 Technology Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| **React 18** | UI library |
| **TypeScript** | Type-safe JavaScript |
| **Vite** | Build tool & dev server |
| **Tailwind CSS** | Utility-first styling |
| **Shadcn/UI** | Component library |
| **React Three Fiber** | 3D graphics (Three.js) |
| **React Router** | Client-side routing |
| **TanStack Query** | Data fetching & caching |

### Backend
| Technology | Purpose |
|------------|---------|
| **Supabase** | Backend-as-a-Service |
| **PostgreSQL** | Database |
| **Edge Functions** | Serverless API endpoints |
| **Row Level Security** | Data protection |

### AI Services
| Service | Purpose |
|---------|---------|
| **OpenAI GPT** | Interview conversation AI |
| **OpenAI Whisper** | Speech-to-text transcription |
| **ElevenLabs** | Text-to-speech voice synthesis |

---

## 🏗 System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        CLIENT (Browser)                          │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐  │
│  │   React UI  │  │  3D Avatar  │  │  Audio Recording/Play   │  │
│  └──────┬──────┘  └──────┬──────┘  └───────────┬─────────────┘  │
│         │                │                      │                │
│         └────────────────┴──────────────────────┘                │
│                          │                                       │
└──────────────────────────┼───────────────────────────────────────┘
                           │ HTTPS
┌──────────────────────────┼───────────────────────────────────────┐
│                    SUPABASE CLOUD                                │
│  ┌───────────────────────┴────────────────────────────────────┐  │
│  │                    Edge Functions                          │  │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │  │
│  │  │interview-chat│  │speech-to-text│  │ text-to-speech   │  │  │
│  │  └──────┬───────┘  └──────┬───────┘  └────────┬─────────┘  │  │
│  └─────────┼─────────────────┼───────────────────┼────────────┘  │
│            │                 │                   │               │
│  ┌─────────┴─────────────────┴───────────────────┴────────────┐  │
│  │                    PostgreSQL Database                     │  │
│  │  ┌──────────┐  ┌────────────────────┐  ┌────────────────┐  │  │
│  │  │ profiles │  │     interviews     │  │interview_msgs  │  │  │
│  │  └──────────┘  └────────────────────┘  └────────────────┘  │  │
│  └────────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────────┘
                           │
         ┌─────────────────┼─────────────────┐
         ▼                 ▼                 ▼
   ┌──────────┐     ┌──────────┐      ┌──────────┐
   │ OpenAI   │     │ OpenAI   │      │ElevenLabs│
   │   GPT    │     │ Whisper  │      │   TTS    │
   └──────────┘     └──────────┘      └──────────┘
```

---

## 💻 Installation & Setup

### Prerequisites
- Node.js 18+ 
- npm or bun
- Git

### Local Development Setup

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/alok-ai-mock.git
cd alok-ai-mock

# 2. Install dependencies
npm install

# 3. Create environment variables
# Create a .env file with:
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_anon_key

# 4. Start development server
npm run dev

# 5. Open in browser
# Navigate to http://localhost:5173
```

### Build for Production

```bash
npm run build
npm run preview
```

---

## 📁 Project Structure

```
alok-ai-mock/
├── public/                    # Static assets
├── src/
│   ├── components/           # React components
│   │   ├── ui/              # Shadcn UI components
│   │   ├── AuthModal.tsx    # Authentication modal
│   │   ├── ChatInterface.tsx # Text interview UI
│   │   ├── ChatMessage.tsx  # Message bubble component
│   │   ├── InterviewerAvatar3D.tsx # 3D avatar
│   │   ├── LiveInterview.tsx # Voice interview UI
│   │   ├── RoleCard.tsx     # Role selection card
│   │   ├── RoleSelection.tsx # Home page
│   │   └── WelcomeHero.tsx  # Welcome section
│   ├── data/
│   │   └── roles.ts         # Interview role definitions
│   ├── hooks/               # Custom React hooks
│   │   ├── useAuth.ts       # Authentication hook
│   │   ├── useAudioRecorder.ts # Audio recording
│   │   ├── useInterviewHistory.ts # History management
│   │   └── useLiveInterview.ts # Live interview logic
│   ├── integrations/
│   │   └── supabase/        # Supabase client & types
│   ├── pages/
│   │   └── Index.tsx        # Main page
│   ├── App.tsx              # Root component
│   ├── index.css            # Global styles & design tokens
│   └── main.tsx             # Entry point
├── supabase/
│   ├── functions/           # Edge functions
│   │   ├── interview-chat/  # AI chat endpoint
│   │   ├── interview-live/  # Live interview endpoint
│   │   ├── speech-to-text/  # Whisper STT endpoint
│   │   └── text-to-speech/  # ElevenLabs TTS endpoint
│   └── config.toml          # Supabase configuration
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── vite.config.ts
```

---

## 🧩 Core Components

### 1. RoleSelection Component
The home page component that displays the welcome message and role selection grid.

**Key Features:**
- Displays "Welcome to Alok AI Mock" branding
- Role selection cards with icons
- Dual mode buttons (Text/Live Interview)
- User authentication dropdown

### 2. LiveInterview Component  
Manages the voice-based interview experience.

**Key Features:**
- 3D AI avatar visualization
- Audio recording and playback
- Real-time transcription
- Interview timer and pause controls

### 3. InterviewerAvatar3D Component
Three.js-powered 3D avatar using React Three Fiber.

**Key Features:**
- Animated sphere with distortion effects
- Particle field animation
- Responsive to speaking/listening states
- Floating animation

### 4. ChatInterface Component
Text-based interview chat interface.

**Key Features:**
- Message history display
- Typing indicators
- Auto-scroll to latest message
- Markdown rendering support

---

## 🗄 Database Schema

### Tables

#### profiles
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| user_id | UUID | Reference to auth.users |
| display_name | TEXT | User display name |
| created_at | TIMESTAMP | Creation timestamp |
| updated_at | TIMESTAMP | Last update timestamp |

#### interviews
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| user_id | UUID | Reference to auth.users |
| role_id | TEXT | Selected role identifier |
| role_title | TEXT | Role display name |
| mode | TEXT | 'text' or 'live' |
| duration_seconds | INTEGER | Interview duration |
| created_at | TIMESTAMP | Creation timestamp |
| updated_at | TIMESTAMP | Last update timestamp |

#### interview_messages
| Column | Type | Description |
|--------|------|-------------|
| id | UUID | Primary key |
| interview_id | UUID | Foreign key to interviews |
| role | TEXT | 'user' or 'assistant' |
| content | TEXT | Message content |
| created_at | TIMESTAMP | Creation timestamp |

### Row Level Security (RLS)
All tables have RLS enabled with policies ensuring users can only access their own data.

---

## 🔌 API Endpoints (Edge Functions)

### 1. interview-chat
Handles text-based interview conversations.

**Request:**
```json
{
  "messages": [
    { "role": "user", "content": "Hello" }
  ],
  "position": "Software Engineer"
}
```

**Response:**
```json
{
  "response": "Hello! Welcome to your interview..."
}
```

### 2. interview-live
Handles live interview with voice synthesis.

**Request:**
```json
{
  "messages": [...],
  "position": "Data Analyst"
}
```

**Response:**
```json
{
  "text": "AI response text",
  "audio": "base64_encoded_audio"
}
```

### 3. speech-to-text
Converts audio to text using OpenAI Whisper.

**Request:**
```json
{
  "audio": "base64_encoded_audio"
}
```

**Response:**
```json
{
  "text": "Transcribed text"
}
```

### 4. text-to-speech
Converts text to audio using ElevenLabs.

**Request:**
```json
{
  "text": "Text to speak"
}
```

**Response:**
```json
{
  "audio": "base64_encoded_audio"
}
```

---

## 🚀 Future Enhancements

1. **Multiple Interviewer Personalities**
   - Strict HR interviewer
   - Supportive mentor
   - Friendly coach

2. **Analytics Dashboard**
   - Performance trends over time
   - Skill improvement tracking
   - Question category analysis

3. **Resume Analysis**
   - Upload resume for personalized questions
   - Role-specific question generation

4. **Video Interview Mode**
   - Camera integration
   - Body language analysis

5. **Interview Scoring**
   - AI-powered response scoring
   - Detailed feedback reports

---

## 👨‍💻 Developer

**Alok** - Full Stack Developer

---

## 📄 License

This project is developed for educational and demonstration purposes.

---

*Documentation generated for seminar presentation*
