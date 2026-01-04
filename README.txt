# PLDE - Procedural Language Drill Engine

**"Automaticity under pressure."**

PLDE is a brutalist, distraction-free web application designed for rapid language acquisition. It ignores gamification trends (XP, gems, avatars) in favor of cognitive science principles: Spaced Repetition, Active Recall, and strict Input Processing.

## Core Philosophy
1.  **Imprint:** See and hear the model.
2.  **Recognition:** Identify the meaning.
3.  **Construction:** Build the sentence structure.
4.  **Production:** Type or speak the answer strictly.
5.  **Chain Linking:** Every 3 links, you are locked in a "Cumulative Review" jail until you get them all correct in a row.

## Setup Guide

### 1. Database (Supabase)
PLDE requires a Supabase backend to store lessons.
1.  Create a project at [supabase.com](https://supabase.com).
2.  Run this SQL to create the table:
    ```sql
    create table lessons (
      id uuid default uuid_generate_v4() primary key,
      created_at timestamp with time zone default timezone('utc'::text, now()) not null,
      title text not null,
      content jsonb not null
    );
    ```
3.  **Important:** Enable Row Level Security (RLS) and create a policy to allow "Select" access to "All Users" (public).

### 2. Configuration
Open `index.html` and update the `SUPABASE_URL` and `SUPABASE_KEY` constants at the top of the script. 
*Note: Use the "Anon" (Public) key, not the Service Role key.*

## Usage
*   **Mobile:** Add to Home Screen for a native app feel.
*   **Voice:** Requires a browser with Web Speech API support (Chrome/Safari/Edge).
*   **Strict Mode:** Punctuation is ignored, but spelling and word order must be exact.

## License
MIT. Build something useful.