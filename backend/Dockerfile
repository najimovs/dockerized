# Development stage
FROM node:24-alpine AS development

# Install pnpm
RUN corepack enable && corepack prepare pnpm@10 --activate

WORKDIR /app

# Copy package files
COPY package.json pnpm-lock.yaml* ./

# Install dependencies
RUN pnpm install --frozen-lockfile

# Copy application code
COPY . .

EXPOSE 3000

CMD ["pnpm", "dev"]

# Production stage
FROM node:24-alpine AS production

RUN corepack enable && corepack prepare pnpm@10 --activate

WORKDIR /app

COPY package.json pnpm-lock.yaml* ./

# Install only production dependencies
RUN pnpm install --frozen-lockfile --prod

COPY . .

EXPOSE 3000

CMD ["pnpm", "start"]
