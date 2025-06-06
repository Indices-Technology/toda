
# TODA Classified Ads Platform - Feature Clarifications

## Ads & Listings

**How should ad weighting be calculated?**  
Ad weighting should prioritize relevant and active listings using a scoring algorithm (normalized to 0–100):  
- **Seller Activity (40%)**: Frequency of logins, ad postings, and response time.  
- **User Interactions (30%)**: Views, bookmarks, and messages.  
- **Ad Quality (20%)**: Completeness (images, descriptions, tags) and verified seller status.  
- **Recency (10%)**: Newer ads get a slight boost.  
Promoted ads receive a 1.5x multiplier for visibility.

**What filters should be included?**  
The advanced filtering system should include:  
- **Category**: Product/service type (e.g., electronics, real estate, services).  
- **Price Range**: Min/max sliders.  
- **Location**: Radius-based (e.g., 5km, 10km) or city/area.  
- **Condition**: New, used, refurbished (for products).  
- **Seller Type**: Individual, business, verified only.  
- **Keywords/Tags**: User-entered or predefined tags.  
- **Sort Options**: Relevance, recency, price (low-high/high-low).  
Filters should be collapsible on mobile with multi-select options.

## User & Safety

**What’s required for seller verification?**  
- **Basic Verification**: Email and phone confirmation.  
- **Standard Verification**: Government-issued ID (e.g., driver’s license, passport) or business registration.  
- **Optional Enhanced Verification**: Video call or selfie with ID for a premium badge.  
Verification is one-time with annual rechecks for active sellers. Verified sellers gain a badge and higher ad weighting.

**How should contact leakage be handled?**  
- **In-App Messaging**: Mandate initial communication via platform chat.  
- **Text Analysis**: Use regex/NLP to block contact info (phone, email, links) until a buyer action.  
- **Warning System**: Notify users for attempts to share info, with restrictions for repeat violations.  
- **Contact Reveal**: Triggered by a buyer action (see below).

**Should reviews allow media uploads?**  
Yes, support up to 3 images or a 15-second video per review to enhance credibility (e.g., before/after photos for services). Admin moderation ensures appropriateness.

## Messaging & Notifications

**Should chat be real-time?**  
Yes, use WebSocket or Firebase for real-time chat with read receipts and typing indicators. Offline messages should sync when users reconnect.

**What triggers contact reveal?**  
Contact info (phone, email) auto-reveals after:  
- **Buyer Commitment**: Confirmed purchase intent (e.g., “Buy Now”).  
- **Seller Approval**: Seller manually approves sharing.  
- **Time-Based**: After 10 messages to ensure platform engagement.  
Admins can override or block reveals if fraud is suspected.

**Should we support email or push notifications?**  
Both:  
- **Push Notifications**: Real-time updates (messages, bookmarks, expiry reminders) via PWA.  
- **Email Notifications**: Weekly summaries, expiry warnings, referral rewards.  
Users can customize settings in their dashboard.

## Search & Discovery

**Preferred map system (Google Maps, Mapbox, etc.)?**  
**Mapbox** for cost-effectiveness, customization, and privacy. Supports interactive maps and radius-based filtering. Use Google Maps as a fallback for premium features if budget allows. Optimize for mobile performance.

**Auto-suggestions: global or personalized?**  
**Personalized auto-suggestions** based on:  
- **User Behavior**: Recent searches, viewed ads, bookmarked categories.  
- **Location**: Nearby listings or local trends.  
- **Platform Trends**: Popular categories globally as fallback.  


## User Dashboard & Admin

**What sections are needed in the user dashboard?**  
- **Overview**: Active ads, bookmarks, unread messages.  
- **My Listings**: View/edit active, expired, or draft ads (sellers).  
- **Bookmarks**: Saved ads with filters.  
- **Messages**: Chat inbox with history.  
- **Ratings & Reviews**: View/submit ratings and reviews.  
- **Profile Settings**: Manage verification, contact info, notifications.  
- **Analytics (Sellers)**: Ad views, clicks, bookmarks, and performance tips.

**What controls should admins have?**  
- **Ad Management**: Approve, reject, or edit reported listings.  
- **User Management**: Ban, suspend, or verify users; review verification documents.  
- **Reports**: Resolve scam/fraud reports with evidence logs.  
- **Analytics**: Platform metrics (active users, ad volume, engagement).  
- **Content Moderation**: Remove violating ads/users.  
- **Notification Tools**: Send bulk messages or alerts.

## Analytics & Referrals

**What seller metrics are essential?**  
- **Ad Performance**: Views, clicks, bookmarks, messages per ad.  
- **Engagement Rate**: Views leading to actions (messages, bookmarks).  
- **Response Time**: Average reply time.  
- **Conversion Rate**: Inquiries leading to contact reveals or sales.  
- **Profile Metrics**: Followers, profile views, rating summary.  
Include visualizations (e.g., line charts) and actionable tips.

**How should referrals and rewards work?**  
- **Referral System**: Unique referral links for new buyers/sellers.  
- **Rewards**: Extended ad duration (+7 days), promoted slots, or credits.  
- **Tracking**: Reward after referred user posts an ad or makes a purchase.  
- **Limits**: Cap at 10 referrals/month to prevent abuse.  
- **Incentives**: Bonus for high-rated or frequent sellers (e.g., free promoted ad after 5 five-star reviews).

## Dev & Tech Stack

**Do you have a preferred tech stack or PWA/native preference?**  
- **Tech Stack**:  
  - **Frontend**: React.js or Vuejs with Tailwind CSS for mobile-first UI.  
  - **Backend**: Node.js/Express or Django; PostgreSQL database.  
  - **Search**: Elasticsearch or Algolia for suggestions.  
  - **Map**: Mapbox API.  
  - **Messaging**: Firebase or WebSocket for real-time chat.  
  - **Hosting**: AWS or Vercel for scalability and PWA support.  
- **Preference**: Flutter for native apps (iOS/Android).

**Should we start with wireframes and DB schema?**  
Yes:  
- **Wireframes**: Low-fidelity mockups for home, ad listing, dashboard, admin panel, and messaging (use Figma/Sketch).  
- **Database Schema**: Tables for Users, Listings, Messages, Ratings, Reviews, Reports, Analytics (PostgreSQL with relations).

**Expected timeline for MVP?**  
With a 3–5 developer team:  
- **Week 1–2**: Analysis, wireframes, DB schema.  
- **Week 3–6**: Core features (ads, filtering, verification, messaging).  
- **Week 7–8**: Map, notifications, admin panel.  
- **Week 9–10**: Testing, bug fixes, UI polish.  
- **Total**: ~10–12 weeks for MVP.
 
