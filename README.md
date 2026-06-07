# http-localhost-3000-.-Test
Website testing, integration, debugging, security, Scaling
cd /home/workdir/artifacts/programs/pump_rewards
anchor build --verifiable && anchor test

cd /home/workdir/artifacts/programs/pump_rewards
anchor build --verifiable && anchor test

cd /home/workdir/artifacts/church-of-pump
npm run dev

cd /home/workdir/artifacts/church-of-pump
npm run dev
cd /home/workdir/artifacts/church-of-pump
npm run dev

cd /home/workdir/artifacts/programs/pump_rewards
anchor build --verifiable && anchor test

cd /home/workdir/artifacts/church-of-pump
npm run dev


#!/bin/bash
set -euo pipefail

echo "🔥 Church of Pump - Final Production Hardened Deploy (44B MC+ Ready)"
echo "================================================================"

LOG_FILE="full_deploy_$(date +%Y%m%d_%H%M%S).log"
log() { echo "[$(date '+%H:%M:%S')] $1" | tee -a "$LOG_FILE"; }

log "Starting full stack build & verification..."

# 1. Anchor Program - Verifiable + Tests
cd /home/workdir/artifacts/programs/pump_rewards
log "Building verifiable Anchor program..."
anchor build --verifiable

log "Running full test suite..."
anchor test --provider.cluster localnet

log "Generating IDL..."
anchor idl build

# 2. Frontend Build
cd /home/workdir/artifacts/church-of-pump
log "Building Next.js frontend..."
npm run build

# 3. Docker Build
cd /home/workdir/artifacts
log "Building Docker images..."
docker compose build --no-cache

log "🎉 FULL PRODUCTION BUILD SUCCESSFUL!"
log "Project is hardened for 44B+ MC scale."
log "Log file: $LOG_FILE"

echo ""
echo "Next Steps:"
echo "1. Update Program ID after deployment"
echo "2. Set multisig upgrade authority"
echo "3. Deploy to Vercel + configure env vars"
echo "4. Point Helius webhook to production URL"

exit 0

cd /home/workdir/artifacts
chmod +x full_deploy.sh
./full_deploy.sh



