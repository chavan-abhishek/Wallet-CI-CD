FROM node:22-slim

WORKDIR /usr/src/app

# Copy app files
COPY package.json package-lock.json turbo.json tsconfig.json ./
COPY apps ./apps
COPY packages ./packages

# Install dependencies
RUN npm install
RUN npm run db:generate
RUN npm run build --filter=apps/user-app

# Set NextAuth environment variables (or use -e during docker run)
ENV NEXTAUTH_SECRET=your-secret
ENV NEXTAUTH_URL=http://localhost:3000

EXPOSE 3000
CMD ["npm", "run", "start-user-app"]
